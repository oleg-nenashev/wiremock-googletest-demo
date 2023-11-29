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
$ ctest --output-on-failure

Test project /c/Users/Oleg/Documents/opensource/wiremock/demo/wiremock-cpp-googletest-demo
    Start 1: MyClientTest.HelloWorld
1/3 Test #1: MyClientTest.HelloWorld ......................   Passed    3.16 sec
    Start 2: MyClientTest.HelloWorldFromResource
2/3 Test #2: MyClientTest.HelloWorldFromResource ..........   Passed    3.26 sec
    Start 3: MyClientTest.HelloWorldFromMissingResource
3/3 Test #3: MyClientTest.HelloWorldFromMissingResource ...   Passed    3.24 sec

100% tests passed, 0 tests failed out of 3

Total Test time (real) =   9.69 sec
```
