- httperf --hog --server=attu4.cs.washington.edu --port=8765 --uri="/search?query=word" --rate=60 --num-conns=600 --num-calls=1 --timeout=5

  Total: connections 277 requests 0 replies 0 test-duration 4.615 s

Connection rate: 60.0 conn/s (16.7 ms/conn, <=27 concurrent connections)
Connection time [ms]: min 0.0 avg 0.0 max 0.0 median 0.0 stddev 0.0
Connection time [ms]: connect 126.2
Connection length [replies/conn]: 0.000

Request rate: 0.0 req/s (0.0 ms/req)
Request size [B]: 0.0

Reply rate [replies/s]: min 0.0 avg 0.0 max 0.0 stddev 0.0 (0 samples)
Reply time [ms]: response 0.0 transfer 0.0
Reply size [B]: header 0.0 content 0.0 footer 0.0 (total 0.0)
Reply status: 1xx=0 2xx=0 3xx=0 4xx=0 5xx=0

CPU time [s]: user 1.36 system 3.25 (user 29.5% system 70.4% total 99.9%)
Net I/O: 0.0 KB/s (0.0*10^6 bps)

- httperf --hog --server=attu4.cs.washington.edu --port=8765 --uri="/search?query=word" --rate=60 --num-conns=3600 --num-calls=1 --timeout=5

  Total: connections 1098 requests 0 replies 0 test-duration 18.295 s

Connection rate: 60.0 conn/s (16.7 ms/conn, <=27 concurrent connections)
Connection time [ms]: min 0.0 avg 0.0 max 0.0 median 0.0 stddev 0.0
Connection time [ms]: connect 81.4
Connection length [replies/conn]: 0.000

Request rate: 0.0 req/s (0.0 ms/req)
Request size [B]: 0.0

Reply rate [replies/s]: min 0.0 avg 0.0 max 0.0 stddev 0.0 (3 samples)
Reply time [ms]: response 0.0 transfer 0.0
Reply size [B]: header 0.0 content 0.0 footer 0.0 (total 0.0)
Reply status: 1xx=0 2xx=0 3xx=0 4xx=0 5xx=0

CPU time [s]: user 6.06 system 12.20 (user 33.1% system 66.7% total 99.8%)
Net I/O: 0.0 KB/s (0.0*10^6 bps)

- httperf --hog --server=attu4.cs.washington.edu --port=8765 --uri="/search?query=word" --rate=600 --num-conns=3600 --num-calls=1 --timeout=5

- httperf --hog --server=attu4.cs.washington.edu --port=8765 --uri="/search?query=word" --rate=100 --num-conns=3600 --num-calls=1 --timeout=5

  Total: connections 275 requests 0 replies 0 test-duration 2.749 s

Connection rate: 100.0 conn/s (10.0 ms/conn, <=26 concurrent connections)
Connection time [ms]: min 0.0 avg 0.0 max 0.0 median 0.0 stddev 0.0
Connection time [ms]: connect 61.7
Connection length [replies/conn]: 0.000

Request rate: 0.0 req/s (0.0 ms/req)
Request size [B]: 0.0

Reply rate [replies/s]: min 0.0 avg 0.0 max 0.0 stddev 0.0 (0 samples)
Reply time [ms]: response 0.0 transfer 0.0
Reply size [B]: header 0.0 content 0.0 footer 0.0 (total 0.0)
Reply status: 1xx=0 2xx=0 3xx=0 4xx=0 5xx=0

CPU time [s]: user 0.84 system 1.90 (user 30.5% system 69.3% total 99.8%)
Net I/O: 0.0 KB/s (0.0*10^6 bps)

- httperf --hog --server=attu4.cs.washington.edu --port=8765 --uri="/search?query=word+forest+computer" --rate=60 --num-conns=3600 --num-calls=1 --timeout=5

  Total: connections 266 requests 0 replies 0 test-duration 4.433 s

Connection rate: 60.0 conn/s (16.7 ms/conn, <=14 concurrent connections)
Connection time [ms]: min 0.0 avg 0.0 max 0.0 median 0.0 stddev 0.0
Connection time [ms]: connect 49.4
Connection length [replies/conn]: 0.000

Request rate: 0.0 req/s (0.0 ms/req)
Request size [B]: 0.0

Reply rate [replies/s]: min 0.0 avg 0.0 max 0.0 stddev 0.0 (0 samples)
Reply time [ms]: response 0.0 transfer 0.0
Reply size [B]: header 0.0 content 0.0 footer 0.0 (total 0.0)
Reply status: 1xx=0 2xx=0 3xx=0 4xx=0 5xx=0

CPU time [s]: user 1.60 system 2.83 (user 36.1% system 63.8% total 99.8%)
Net I/O: 0.0 KB/s (0.0*10^6 bps)

- httperf --hog --server=attu4.cs.washington.edu --port=8765 --uri="/search?query=word+forest+computer+apple+window" --rate=60 --num-conns=3600 --num-calls=1 --timeout=5

  Total: connections 302 requests 0 replies 0 test-duration 5.023 s

Connection rate: 60.1 conn/s (16.6 ms/conn, <=19 concurrent connections)
Connection time [ms]: min 0.0 avg 0.0 max 0.0 median 0.0 stddev 0.0
Connection time [ms]: connect 38.7
Connection length [replies/conn]: 0.000

Request rate: 0.0 req/s (0.0 ms/req)
Request size [B]: 0.0

Reply rate [replies/s]: min 0.0 avg 0.0 max 0.0 stddev 0.0 (1 samples)
Reply time [ms]: response 0.0 transfer 0.0
Reply size [B]: header 0.0 content 0.0 footer 0.0 (total 0.0)
Reply status: 1xx=0 2xx=0 3xx=0 4xx=0 5xx=0

CPU time [s]: user 1.93 system 3.08 (user 38.5% system 61.2% total 99.7%)
Net I/O: 0.0 KB/s (0.0*10^6 bps)

- httperf --hog --server=attu4.cs.washington.edu --port=8765 --uri="/search?query=word+forest+computer+apple+window+BooKs+FootBAlL" --rate=60 --num-conns=3600 --num-calls=1 --timeout=5

  Total: connections 310 requests 0 replies 0 test-duration 5.155 s

Connection rate: 60.1 conn/s (16.6 ms/conn, <=22 concurrent connections)
Connection time [ms]: min 0.0 avg 0.0 max 0.0 median 0.0 stddev 0.0
Connection time [ms]: connect 68.1
Connection length [replies/conn]: 0.000

Request rate: 0.0 req/s (0.0 ms/req)
Request size [B]: 0.0

Reply rate [replies/s]: min 0.0 avg 0.0 max 0.0 stddev 0.0 (1 samples)
Reply time [ms]: response 0.0 transfer 0.0
Reply size [B]: header 0.0 content 0.0 footer 0.0 (total 0.0)
Reply status: 1xx=0 2xx=0 3xx=0 4xx=0 5xx=0

CPU time [s]: user 1.76 system 3.39 (user 34.1% system 65.7% total 99.8%)
Net I/O: 0.0 KB/s (0.0*10^6 bps)

- httperf --hog --server=attu4.cs.washington.edu --port=8765 --uri="/search?query=word+forest+computer+apple+window+BooKs+FootBAlL" --rate=100 --num-conns=3600 --num-calls=1 --timeout=5

- Total: connections 548 requests 0 replies 0 test-duration 5.479 s

Connection rate: 100.0 conn/s (10.0 ms/conn, <=27 concurrent connections)
Connection time [ms]: min 0.0 avg 0.0 max 0.0 median 0.0 stddev 0.0
Connection time [ms]: connect 59.8
Connection length [replies/conn]: 0.000

Request rate: 0.0 req/s (0.0 ms/req)
Request size [B]: 0.0

Reply rate [replies/s]: min 0.0 avg 0.0 max 0.0 stddev 0.0 (1 samples)
Reply time [ms]: response 0.0 transfer 0.0
Reply size [B]: header 0.0 content 0.0 footer 0.0 (total 0.0)
Reply status: 1xx=0 2xx=0 3xx=0 4xx=0 5xx=0

CPU time [s]: user 1.68 system 3.79 (user 30.6% system 69.2% total 99.8%)
Net I/O: 0.0 KB/s (0.0*10^6 bps)

- httperf --hog --server=attu4.cs.washington.edu --port=8765 --uri="/search?query=word" --rate=100 --num-conns=3600 --num-calls=1 --timeout=5

- Total: connections 560 requests 0 replies 0 test-duration 5.593 s

Connection rate: 100.1 conn/s (10.0 ms/conn, <=4 concurrent connections)
Connection time [ms]: min 0.0 avg 0.0 max 0.0 median 0.0 stddev 0.0
Connection time [ms]: connect 16.1
Connection length [replies/conn]: 0.000

Request rate: 0.0 req/s (0.0 ms/req)
Request size [B]: 0.0

Reply rate [replies/s]: min 0.0 avg 0.0 max 0.0 stddev 0.0 (1 samples)
Reply time [ms]: response 0.0 transfer 0.0
Reply size [B]: header 0.0 content 0.0 footer 0.0 (total 0.0)
Reply status: 1xx=0 2xx=0 3xx=0 4xx=0 5xx=0

CPU time [s]: user 2.14 system 3.43 (user 38.3% system 61.4% total 99.7%)
Net I/O: 0.0 KB/s (0.0*10^6 bps)

- httperf --hog --server=attu4.cs.washington.edu --port=8765 --uri="/search?query=word" --rate=110 --num-conns=3600 --num-calls=1 --timeout=5

- Total: connections 610 requests 0 replies 0 test-duration 5.546 s

Connection rate: 110.0 conn/s (9.1 ms/conn, <=6 concurrent connections)
Connection time [ms]: min 0.0 avg 0.0 max 0.0 median 0.0 stddev 0.0
Connection time [ms]: connect 16.0
Connection length [replies/conn]: 0.000

Request rate: 0.0 req/s (0.0 ms/req)
Request size [B]: 0.0

Reply rate [replies/s]: min 0.0 avg 0.0 max 0.0 stddev 0.0 (1 samples)
Reply time [ms]: response 0.0 transfer 0.0
Reply size [B]: header 0.0 content 0.0 footer 0.0 (total 0.0)
Reply status: 1xx=0 2xx=0 3xx=0 4xx=0 5xx=0

CPU time [s]: user 2.06 system 3.46 (user 37.1% system 62.3% total 99.5%)
Net I/O: 0.0 KB/s (0.0*10^6 bps)
