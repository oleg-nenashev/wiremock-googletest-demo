# Using WireMock with Testcontainers for C/C++ in Google Test

Yes, you can use WireMock in C/C++ projects!
For that, we can leverage Docker and [Testcontainers for C/C++](https://github.com/testcontainers/testcontainers-c).

This demo shows usage of _Testcontainers for C/C++_
in [Google Test](https://github.com/google/googletest).
For package management we use [CPM.cmake](https://github.com/cpm-cmake/CPM.cmake),
so the library will be built locally for the target platform.

See [test.cpp](./test.cpp) for the code.

## Run the demo

```bash
cmake .
cmake --build .
cd demo/google-test
ctest --output-on-failure
```

## Sample output

```shell
onenashev:~/testcontainers-c/demo/google-test$ ctest --output-on-failure
Test project /home/onenashev/testcontainers-c/demo/google-test
    Start 1: WireMockTestContainer.HelloWorld
1/5 Test #1: WireMockTestContainer.HelloWorld ......................   Passed    3.31 sec
    Start 2: WireMockTestContainer.HelloWorldFromResource
2/5 Test #2: WireMockTestContainer.HelloWorldFromResource ..........   Passed    3.97 sec
    Start 3: WireMockTestContainer.HelloWorldFromMissingResource
3/5 Test #3: WireMockTestContainer.HelloWorldFromMissingResource ...   Passed    3.91 sec

100% tests passed, 0 tests failed out of 3
```
