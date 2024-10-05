# Specify the minimum version of CMake required
cmake_minimum_required(VERSION 3.10)

# Define the project name
project(HelloWorld)

find_package(PkgConfig REQUIRED)
pkg_check_modules(ADDITION REQUIRED addition-lib)

# Add an executable target for the hello.c file
add_executable(hello hello.cpp)

target_link_libraries(hello PUBLIC ${ADDITION_LIBRARIES})
target_include_directories(hello PUBLIC ${ADDITION_INCLUDE_DIRS})

install(TARGETS hello)
