

```bash
cmake -S . -B build
cmake --build build
cd build && ctest
```


The solution: add library to CMakeLists
```bash
add_library(sample1 sample1.h sample1.cc)

add_executable(
  sample1_unittest
  sample1_unittest.cc
)
```