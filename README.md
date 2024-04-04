# Main Functions
TODO

# check some -> simulate session check

# void* and all the cast
Below code trying to cast a void* into int32_t
```
  // hw3/WriteIndex.cc
  // STEP 14.
  // Truncate to 32 bits, then convert it to network order and write it out.
  int64_t pos = reinterpret_cast<int64_t>(tmp);
  position.position = static_cast<int32_t>(pos);
  position.ToDiskFormat();
```

It can't be like this which cause seg fault
```
position.position = static_cast<int32_t>(tmp);
```
Knowledges here:

-  reinterpret_cast : same size but different type (void* -> int64_t)
   static_cast : same type but big size to small size (int64_t -> int32_t) (reverse will cause data loss)

- store a value in a void* pointer
```
ElementType value = /* ... */;
uintptr_t intermediate = static_cast<uintptr_t>(value);
void* ptr = reinterpret_cast<void*>(intermediate);

// If you do know you're in 64-system or the pointer is big enough, you can do this
ElementType value = /* ... */;
void* ptr = reinterpret_cast<void*>(value);
```
uintptr_t -> 1 make sure you get all data 2 avoid memory alignment issues


# why void* as paypoad_t

Although void* is not safe for cross-platform (if you use int64_t in 32 system with void*, you will lose data since void* is 32 in 32-system)

It does have some pros:

- to create general data structures. Later on the linkedlist will be use in many situations.

- we know c doesn't have overload. So some POSIX function like fwrite() will take a void* to handle different calls.

- allow storing value / address
```
// store address
typedef struct {
  int num;
} ExamplePayload;

payload = (ExamplePayload *) malloc(sizeof(ExamplePayload));
payload->num = 10;
LinkedList_Push(list, (LLPayload_t)payload);

// store address
int32_t *num = new int32_t(10);
LinkedList_Push(list, (LLPayload_t)num);

// store value
int32_t num = 10;
Linkedlist_Push(list, (LLPayload_t)(int64_t)num);

// store value
int num = 10;
LinkedList_Push(list, (LLPayload_t)(uintptr_t)num);
```
several tips:

1) we dont need (int64_t*) fro the second one, because the pointer size is always 64/32, same with void* and depends on the paltform you're in.
2) for the third one, use uintptr_t to safely transform.

In short, Increase flexibility where I manually keep it safe.


# free

sometimes just call free(), sometimes need to define a payload_free_function.

First we have:
```
typedef void(*LLPayloadFreeFnPtr)(LLPayload_t payload);
LLPayloadFreeFnPtr op = somefn;

// rather than do this every time:
void (*op)(LLPayload_t payload);
op = somefn;
```

free -> free thing we get from malloc, including regular struct.

free_fn -> complex struct which have pointer inside

noNp_free -> example1 : hashmap resize. free the struct while keeping the elements.

example2 : free hashtable, we first use kv_free_fn to free every kv_value of a list, and use LinkedList_Free(list, LLNoOpFree); to free the list.

# idea of manage ownership explicitly

give by passing in as args, or get by return value as args.

# linkedList_priv.h & linkedList.h

use private header file

- some node struct definition can be import to many .c files.
- keep hiding from the use as put them in .c
- reduce unnecessary re-compile rather than put then in .h

an example: unittest can peek into the header_priv.h, inside the implementation to verify correctness.

# System calls
```
static void HandleDir(char* dir_path, DIR* d, DocTable** doc_table, MemIndex** index) {
  struct dirent* dirent;
  struct stat st;

  // 第一阶段：收集目录中所有条目的信息
  while ((dirent = readdir(d)) != NULL) {  // 使用 readdir 读取目录条目
    if (strcmp(dirent->d_name, ".") == 0 || strcmp(dirent->d_name, "..") == 0) {
      continue;  // 忽略 "." 和 ".." 目录
    }

    // 构造完整路径名以用于 stat 调用
    char* full_path;  // 分配内存并构造 full_path

    if (stat(full_path, &st) == 0) {  // 使用 stat 获取条目信息
      if (S_ISREG(st.st_mode)) {
        // 处理普通文件
      } else if (S_ISDIR(st.st_mode)) {
        // 处理子目录
      } else {
        // 忽略非文件非目录的条目
      }
    }
    free(full_path);  // 释放 full_path 分配的内存
  }

  // 第二阶段：按字母顺序处理已排序的目录元数据
  // 排序目录条目（这需要一个结构来存储条目的详细信息）

  for (int i = 0; i < num_entries; i++) {  // 处理每个条目
    if (!entries[i].is_dir) {
      // 处理文件
    } else {
      DIR* sub_dir = opendir(entries[i].path_name);  // 使用 opendir 打开子目录
      if (sub_dir != NULL) {
        HandleDir(entries[i].path_name, sub_dir, doc_table, index);  // 递归调用处理子目录
        closedir(sub_dir);  // 使用 closedir 关闭子目录
      }
    }
    // 清理，例如释放分配的内存
  }
  // 清理，在此处释放分配的资源
}
```


# inheritance and offset

function pointer -> dynamiv biding

hashtable reader and driver class -> inheritance (keep lookupBucket, add lookupDocid...)

fseek+fwrite the element, and fseek to header to store the size -> offset.

# hw4
- 为什么集成ServerSocket类？

  保存listen_sock_fd, port, ai_family，并且集成Accpect，在其中调用accpet()，两层while可以实现一直监听并在接收到时分配给一个线程处理。

- <img width="765" alt="image" src="https://github.com/Yzhonghua/FileSearchEngineMirror/assets/59692712/7fba5069-983f-4848-9f00-99ce94854af1">

- 一个ip:port仅能对应一个listen_sock_fd，有类似表的结构进行管理。当然也可以设置快速回收避免time_wait（并不意味着同一时间有两个socket，只是可以绑定两个）：
```
// allow recycle immediately
int optval = 1;
setsockopt(_listen_fd, SOL_SOCKET, SO_REUSEADDR,
           &optval, sizeof(optval));
```

- HttpConnection: getNextRequest, parseRequest, WriteResponse

- HttpServer: listen_sock_fd + ServerTask, 调用hc, processRequest (file / url), 调用hc

- 一些与http层面无关的小工具集成在HttpUtils中，比如wrappedRead, wrappedWrite, urlParser, fileReader以及检查安全性的两个方法。
