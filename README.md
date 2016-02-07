project_test
============

This is a skeleton of a C++ project.
The project is using the following tools:
    
* Test Framework: Google Test
* Documentation Gen: Sphinx
* Build Tool: CMake
* Version Control System: Git
* Dependencies: CMake + [(Git & gitmodules)(*)]
* Performance: Hayai(**)

(*) (**) subject to change in a near future
(*) because of Code redundancy most people will use the lastest working
version which means there is no need for each projects to have their own
gtest(or else) repo (10 projects = 10 identical copies of gtest ? Noway)

# Configuration

## Directory Layout

* src/          : Project Code source
* cmake/        : CMake Scripts (FindXXX.cmake)
* tests/        : Tests files (***_test.cpp)
* benchmark/    : Performance tests (***_bench.cpp)
* docs/         : Doxygen or Sphinx files
* data/         : Data (Used to store Performance results for each git commit)
* build/        : git ignored folder in which you can build the project
* dependencies/ : Dependencies source code

## Benchmark
    
When checking your application performance you may want to check against previous
performance. This is why 'Benchmark' save execution time per commit so performance
evolution can be easily tracked.

# How to

## Create a library/executable

* create a new folder 'src/new_library' or 'src/new_exec'
* add 'src/new_library/src/CMakeLists.txt'
* create library files (.cpp and .h)
* create new CMake variable with library's files 
    
    SET(MY_LIBRARY_SRC
            file1.h
            file1.cpp
            file2.h
            file2.cpp
    )
    
* Add the compile command:
    
    ADD_LIBRARY(my_library ${MY_LIBRARY_SRC})
    SET_PROPERTY(TARGET my_library PROPERTY CXX_STANDARD 11)
    
OR
    ADD_EXECUTABLE(my_exec ${MY_LIBRARY_SRC})  
    TARGET_LINK_LIBRARIES(my_exec dependencies)
    SET_PROPERTY(TARGET my_exec PROPERTY CXX_STANDARD 11)
    
## Add tests

* create a new file 'my_newtest_test.cpp'
* add TEST_MACRO(my_newtest) at the end of the file 'tests/CMakeLists.txt'

## Add Benchmark

* create a new file 'my_newbench_bench.cpp'
* add TEST_BENCH(my_newbench) at the end of the file 'benchmark/CMakeLists.txt'

## Add (to be compiled) Dependencies

* open git bash
* go to the project repo
* git submodule add url_to_dependency_repo dependencies/library_name

Example: add opencv to the project

    git submodule add https://github.com/Itseez/opencv.git dependencies/opencv
    
## Add pre-compiled Dependencies

* Add FindXXX.cmake script in the cmake/ folder
* Add FIND_PACKAGE(XXX) in ./CMakeLists.txt
    
    
TODO
====

* How to
* Profiling
* Valgrind utils/Sanitizer Command/debbuger
* Doc
* how to activate optimization on CMake
* Goole Perf ?
* Nonius ? <== Need to be updated
* hayai ?
* Configuration files
* Generated files


