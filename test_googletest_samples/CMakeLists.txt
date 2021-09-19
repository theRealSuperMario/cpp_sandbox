cmake_minimum_required(VERSION 3.14)
project(googletest_samples)

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

include(GoogleTest)


enable_testing()

add_library(sample1 sample1.h sample1.cc)

add_executable(
  sample1_unittest
  sample1_unittest.cc
)

target_link_libraries(
  sample1_unittest
  gtest_main
  sample1
)

gtest_discover_tests(sample1_unittest)