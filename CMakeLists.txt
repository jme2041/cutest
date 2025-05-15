# CMakeLists.txt
# cutest: C Unit Testing Framework

cmake_minimum_required(VERSION 3.31)
project(cutest LANGUAGES C VERSION 1.5.0.0)
set(CMAKE_C_STANDARD 17)

add_library(cutest STATIC "src/CuTest.c")

target_include_directories(cutest PUBLIC "include")

if(CUTEST_TESTS)
    add_executable(test_cutest "test/AllTests.c" "test/CuTestTest.c")
    add_dependencies(test_cutest cutest)
    target_link_libraries(test_cutest PRIVATE cutest)
endif()

###############################################################################
