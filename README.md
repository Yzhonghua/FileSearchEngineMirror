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

In short, Increase flexibility where I manually keep it safe.


# free

sometimes just call free(), sometimes need to define a payload_free_function.

# idea of manage ownership explicitly

give by passing in as args, or get by return value as args.
