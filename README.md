# Valgrind Exercise

## Standard install via command-line
```bash
# Configure the project and generate a native build system:
  # Must re-run this command whenever any CMakeLists.txt file has been changed.
  cmake -S ./ -B build/
# Compile and build the project:
  # rebuild only files that are modified since the last build
  cmake --build build/
  # or rebuild everything from scracth
  cmake --build build/ --clean-first
  # to see verbose output, do:
  cmake --build build/ --verbose
# Run program:
  ./build/app/shell-app
# Clean
  cmake --build build/ --target clean
# Clean and start over:
  rm -rf build/
```


# Extra Credit Questions:

## What happens when the executable is linked statically?  
An executable that is linked statically is self-contained and does not rely on outside shared libraries because all required libraries and dependencies are built into the executable itself. Because static linking doesn't rely on certain library versions installed on the destination system, it results in a bigger binary file but can make the executable more portable.

## Does Valgrind still detect those same bugs? Why or why not.
Although its capabilities are more constrained when compared to its analysis of dynamically linked executables, Valgrind may detect memory problems, such as memory leaks, in statically linked executables.Regardless of whether the binary is statically or dynamically linked, Memcheck acts at the level of individual memory accesses. It can keep track of memory allocations, deallocations, and read/write activities. This simple memory analysis can be used to find memory-related issues in both kinds of executables. By keeping track of memory allocations and deallocations, it can also find memory leaks in statically linked executables. Furthermore, in statically linked executables, Valgrind can carry out heap checks, a type of memory leak detection. It can spot memory blocks that haven't been properly released and flag them as potential memory leaks.
