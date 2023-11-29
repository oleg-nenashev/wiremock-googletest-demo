# Google Test demo
# This is based on https://google.github.io/googletest/quickstart-cmake.html
cmake_minimum_required (VERSION 3.16.3)
project(wiremock-googletest-demo
    VERSION 0.0.1
    DESCRIPTION "Demonstrates usage of WireMock with Testcontainers for C/C++ in Google Test")
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(TARGET_OUT ${PROJECT_NAME}.out)

include(cmake/CPM.cmake)
CPMAddPackage(
    NAME testcontainers-c
    VERSION 0.0.2
    GITHUB_REPOSITORY "testcontainers/testcontainers-c"
    OPTIONS "SKIP_DEMOS TRUE")

# GoogleTest v1.14.0
include(FetchContent)
FetchContent_Declare(
    googletest
    URL https://github.com/google/googletest/archive/f8d7d77c06936315286eb55f8de22cd23c188571.zip
)
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)

enable_testing()
file(COPY test_data DESTINATION ${CMAKE_CURRENT_BINARY_DIR})

add_executable(${TARGET_OUT} MyClientTest.cpp)
add_dependencies(${TARGET_OUT} testcontainers-c-shim)
target_link_libraries(${TARGET_OUT} PRIVATE testcontainers-c)
target_link_libraries(${TARGET_OUT} PRIVATE GTest::gtest_main)

include(GoogleTest)
# FIXME Testcontainers for C/C++ fails when tests are launched as a sub-module
gtest_discover_tests(${TARGET_OUT})
