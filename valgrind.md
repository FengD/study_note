## Valgrind Study

##Tools

`Valgrind`是一个二进制插桩框架，可以用来制作二进制分析工具。利用Valgrind可以检测二进制程序的内存和线程漏洞。Valgrind框架目前包含以下几种工具：

* `Memcheck` is a memory error detector. It helps you make your programs, particularly those written in C and C++, more correct.

* `Cachegrind` is a cache and branch-prediction profiler. It helps you make your programs run faster.

* `Callgrind` is a call-graph generating cache profiler. It has some overlap with Cachegrind, but also gathers some information that Cachegrind does not.

* `Helgrind` is a thread error detector. It helps you make your multi-threaded programs more correct.

* `DRD` is also a thread error detector. It is similar to Helgrind but uses different analysis techniques and so may find different problems.

* `Massif` is a heap profiler. It helps you make your programs use less memory.

* `DHAT` is a different kind of heap profiler. It helps you understand issues of block lifetimes, block utilisation, and layout inefficiencies.

* `SGcheck` is an experimental tool that can detect overruns of stack and global arrays. Its functionality is complementary to that of Memcheck: SGcheck finds problems that Memcheck can't, and vice versa..

* `BBV` is an experimental SimPoint basic block vector generator. It is useful to people doing computer architecture research and development.
