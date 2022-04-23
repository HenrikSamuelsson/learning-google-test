cmake_minimum_required(VERSION 3.14)
project(google-test-quick-start-cmake)

# GoogleTest requires at least C++11
set(CMAKE_CXX_STANDARD 11)

include(FetchContent)
FetchContent_Declare(
  googletest
  URL https://github.com/google/googletest/archive/609281088cfefc76f9d0ce82e1ff6c30cc3591e5.zip
)

# For Windows: Prevent overriding the parent project's compiler/linker settings
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)

# Enable testing in CMake
enable_testing()

# The test binary to build
add_executable(
  hello_test
  hello_test.cc
)

# Link to GoogleTest
target_link_libraries(
  hello_test
  gtest_main
)

# Enable CMake's test runner to discover test in the binary
include(GoogleTest)
gtest_discover_tests(hello_test)