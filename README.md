# Benchmark cloud servers

## Servers

- DigitalOcean 2 vCPU/4 GB (20$/month)
- OVH S1-8 (2 vCPU/8 GB) (13€/month)
- Vultr 2 vCPU/4 GB (20$/month)
- Scaleway START1-S (2 vCPU/2 GB) (4€/month)

## Configuration

```
# cat /etc/centos-release
CentOS Linux release 7.4.1708 (Core)
```

```
# uname -a
Linux centos-s-2vcpu-4gb-ams2-01 3.10.0-693.21.1.el7.x86_64 #1 SMP Wed Mar 7 19:03:37 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

```
# sysbench --version
sysbench 1.0.14
```

## Results

| Component | DigitalOcean | OVH | Vultr | Scaleway | Winner |
|-----------|--------------|-----|-------|----------|--------|
| CPU (events/s) | 6136.55 | 7583.36 | 9762.53 |  | DigitalOcean |
| Memory (MiB/s) | 3327.92 | 4132.54 | 1378.09 |  | OVH | 
| Disk (reads/s) | 1958.16 | 426.19 | 1489.38 |  | DigitalOcean |
| Disk (writes/s) | 1305.44 | 284.13 | 992.92 |  | DigitalOcean |
| Disk (read MiB/s) | 30.60 | 6.66 | 23.27 |  | DigitalOcean |
| Disk (write MiB/s) | 20.40 | 4.44 | 15.51 |  | DigitalOcean |
| Network (Mbits/sec) | 913 | 102 | 3730 |  | Vultr |

## Tests

### CPU

DigitalOcean
```
# sysbench cpu --cpu-max-prime=2000 run
sysbench 1.0.14 (using bundled LuaJIT 2.1.0-beta2)

Running the test with following options:
Number of threads: 1
Initializing random number generator from current time


Prime numbers limit: 2000

Initializing worker threads...

Threads started!

CPU speed:
    events per second:  6136.55

General statistics:
    total time:                          10.0002s
    total number of events:              61383

Latency (ms):
         min:                                    0.14
         avg:                                    0.16
         max:                                    1.29
         95th percentile:                        0.20
         sum:                                 9961.26

Threads fairness:
    events (avg/stddev):           61383.0000/0.00
    execution time (avg/stddev):   9.9613/0.00
```

OVH
```
# sysbench cpu --cpu-max-prime=2000 run
sysbench 1.0.14 (using bundled LuaJIT 2.1.0-beta2)

Running the test with following options:
Number of threads: 1
Initializing random number generator from current time


Prime numbers limit: 2000

Initializing worker threads...

Threads started!

CPU speed:
    events per second:  7583.36

General statistics:
    total time:                          10.0002s
    total number of events:              75863

Latency (ms):
         min:                                    0.10
         avg:                                    0.13
         max:                                    0.33
         95th percentile:                        0.15
         sum:                                 9973.62

Threads fairness:
    events (avg/stddev):           75863.0000/0.00
    execution time (avg/stddev):   9.9736/0.00
```

Vultr
```
# sysbench cpu --cpu-max-prime=2000 run
sysbench 1.0.14 (using bundled LuaJIT 2.1.0-beta2)

Running the test with following options:
Number of threads: 1
Initializing random number generator from current time


Prime numbers limit: 2000

Initializing worker threads...

Threads started!

CPU speed:
    events per second:  9762.53

General statistics:
    total time:                          10.0004s
    total number of events:              97645

Latency (ms):
         min:                                    0.00
         avg:                                    0.10
         max:                                    3.20
         95th percentile:                        0.12
         sum:                                 9917.67

Threads fairness:
    events (avg/stddev):           97645.0000/0.00
    execution time (avg/stddev):   9.9177/0.00
```

Scaleway
```
```

### Memory

DigitalOcean
```
# sysbench memory --threads=2 run
sysbench 1.0.14 (using bundled LuaJIT 2.1.0-beta2)

Running the test with following options:
Number of threads: 2
Initializing random number generator from current time


Running memory speed test with the following options:
  block size: 1KiB
  total size: 102400MiB
  operation: write
  scope: global

Initializing worker threads...

Threads started!

Total operations: 34087979 (3407794.18 per second)

33289.04 MiB transferred (3327.92 MiB/sec)


General statistics:
    total time:                          10.0001s
    total number of events:              34087979

Latency (ms):
         min:                                    0.00
         avg:                                    0.00
         max:                                    0.26
         95th percentile:                        0.00
         sum:                                 9869.79

Threads fairness:
    events (avg/stddev):           17043989.5000/15071.50
    execution time (avg/stddev):   4.9349/0.00
```

OVH
```
# sysbench memory --threads=2 run
sysbench 1.0.14 (using bundled LuaJIT 2.1.0-beta2)

Running the test with following options:
Number of threads: 2
Initializing random number generator from current time


Running memory speed test with the following options:
  block size: 1KiB
  total size: 102400MiB
  operation: write
  scope: global

Initializing worker threads...

Threads started!

Total operations: 42326739 (4231723.10 per second)

41334.71 MiB transferred (4132.54 MiB/sec)


General statistics:
    total time:                          10.0001s
    total number of events:              42326739

Latency (ms):
         min:                                    0.00
         avg:                                    0.00
         max:                                    1.19
         95th percentile:                        0.00
         sum:                                10072.07

Threads fairness:
    events (avg/stddev):           21163369.5000/16064.50
    execution time (avg/stddev):   5.0360/0.00
```

Vultr
```
# sysbench memory --threads=2 run
sysbench 1.0.14 (using bundled LuaJIT 2.1.0-beta2)

Running the test with following options:
Number of threads: 2
Initializing random number generator from current time


Running memory speed test with the following options:
  block size: 1KiB
  total size: 102400MiB
  operation: write
  scope: global

Initializing worker threads...

Threads started!

Total operations: 14114326 (1411168.18 per second)

13783.52 MiB transferred (1378.09 MiB/sec)


General statistics:
    total time:                          10.0001s
    total number of events:              14114326

Latency (ms):
         min:                                    0.00
         avg:                                    0.00
         max:                                    8.18
         95th percentile:                        0.00
         sum:                                 8083.76

Threads fairness:
    events (avg/stddev):           7057163.0000/214370.00
    execution time (avg/stddev):   4.0419/0.01
```

Scaleway
```
```


### Disk

DigitalOcean
```
# sysbench --test=fileio --file-total-size=30G --file-test-mode=rndrw --max-time=300 --max-requests=0 run
WARNING: the --test option is deprecated. You can pass a script name or path on the command line without any options.
WARNING: --max-time is deprecated, use --time instead
sysbench 1.0.14 (using bundled LuaJIT 2.1.0-beta2)

Running the test with following options:
Number of threads: 1
Initializing random number generator from current time


Extra file open flags: (none)
128 files, 240MiB each
30GiB total file size
Block size 16KiB
Number of IO requests: 0
Read/Write ratio for combined random IO test: 1.50
Periodic FSYNC enabled, calling fsync() each 100 requests.
Calling fsync() at the end of test, Enabled.
Using synchronous I/O mode
Doing random r/w test
Initializing worker threads...

Threads started!


File operations:
    reads/s:                      1958.16
    writes/s:                     1305.44
    fsyncs/s:                     4177.37

Throughput:
    read, MiB/s:                  30.60
    written, MiB/s:               20.40

General statistics:
    total time:                          300.0059s
    total number of events:              2232356

Latency (ms):
         min:                                    0.00
         avg:                                    0.13
         max:                                   56.58
         95th percentile:                        0.48
         sum:                               297615.46

Threads fairness:
    events (avg/stddev):           2232356.0000/0.00
    execution time (avg/stddev):   297.6155/0.00
```

OVH
```
# sysbench --test=fileio --file-total-size=30G --file-test-mode=rndrw --max-time=300 --max-requests=0 run
WARNING: the --test option is deprecated. You can pass a script name or path on the command line without any options.
WARNING: --max-time is deprecated, use --time instead
sysbench 1.0.14 (using bundled LuaJIT 2.1.0-beta2)

Running the test with following options:
Number of threads: 1
Initializing random number generator from current time


Extra file open flags: (none)
128 files, 240MiB each
30GiB total file size
Block size 16KiB
Number of IO requests: 0
Read/Write ratio for combined random IO test: 1.50
Periodic FSYNC enabled, calling fsync() each 100 requests.
Calling fsync() at the end of test, Enabled.
Using synchronous I/O mode
Doing random r/w test
Initializing worker threads...

Threads started!


File operations:
    reads/s:                      426.19
    writes/s:                     284.13
    fsyncs/s:                     908.95

Throughput:
    read, MiB/s:                  6.66
    written, MiB/s:               4.44

General statistics:
    total time:                          300.0012s
    total number of events:              485788

Latency (ms):
         min:                                    0.00
         avg:                                    0.62
         max:                                   37.14
         95th percentile:                        1.50
         sum:                               299088.03

Threads fairness:
    events (avg/stddev):           485788.0000/0.00
    execution time (avg/stddev):   299.0880/0.00
```

Vultr
```
# sysbench --test=fileio --file-total-size=30G --file-test-mode=rndrw --max-time=300 --max-requests=0 run
WARNING: the --test option is deprecated. You can pass a script name or path on the command line without any options.
WARNING: --max-time is deprecated, use --time instead
sysbench 1.0.14 (using bundled LuaJIT 2.1.0-beta2)

Running the test with following options:
Number of threads: 1
Initializing random number generator from current time


Extra file open flags: (none)
128 files, 240MiB each
30GiB total file size
Block size 16KiB
Number of IO requests: 0
Read/Write ratio for combined random IO test: 1.50
Periodic FSYNC enabled, calling fsync() each 100 requests.
Calling fsync() at the end of test, Enabled.
Using synchronous I/O mode
Doing random r/w test
Initializing worker threads...

Threads started!


File operations:
    reads/s:                      1489.38
    writes/s:                     992.92
    fsyncs/s:                     3177.02

Throughput:
    read, MiB/s:                  23.27
    written, MiB/s:               15.51

General statistics:
    total time:                          300.0002s
    total number of events:              1697822

Latency (ms):
         min:                                    0.00
         avg:                                    0.18
         max:                                   17.76
         95th percentile:                        0.54
         sum:                               298082.69

Threads fairness:
    events (avg/stddev):           1697822.0000/0.00
    execution time (avg/stddev):   298.0827/0.00
```

Scaleway
```
```


### Public network (download)

DigitalOcean
```
# iperf -c iperf -c bouygues.iperf.fr
------------------------------------------------------------
Client connecting to bouygues.iperf.fr, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 37.139.0.143 port 57786 connected with 89.84.1.222 port 5001
write failed: Connection reset by peer
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 8.2 sec   889 MBytes   913 Mbits/sec
```

DigitalOcean Optimized
```
# iperf -c iperf -c bouygues.iperf.fr
------------------------------------------------------------
Client connecting to bouygues.iperf.fr, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 174.138.3.20 port 48170 connected with 89.84.1.222 port 5001
write failed: Connection reset by peer
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 4.5 sec   887 MBytes  1.64 Gbits/sec
```

OVH
```
# iperf -c iperf -c bouygues.iperf.fr
------------------------------------------------------------
Client connecting to bouygues.iperf.fr, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 54.38.247.83 port 36080 connected with 89.84.1.222 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.1 sec   123 MBytes   102 Mbits/sec
```

Vultr
```
# iperf -c bouygues.iperf.fr
------------------------------------------------------------
Client connecting to bouygues.iperf.fr, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 108.61.176.130 port 39338 connected with 89.84.1.222 port 5001
write failed: Connection reset by peer
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 2.0 sec   887 MBytes  3.73 Gbits/sec
```

Scaleway
```
```
