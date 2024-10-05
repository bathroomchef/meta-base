# Specify the minimum version of CMake required
cmake_minimum_required(VERSION 3.10)

# Define the project name
project(HelloWorld)

add_library(addition-lib STATIC ${CMAKE_CURRENT_SOURCE_DIR}/src/add.cpp)
target_include_directories(addition-lib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/inc)

install(TARGETS addition-lib LIBRARY DESTINATION lib)

install(DIRECTORY inc/ DESTINATION include)

configure_file(addition-lib.pc.in addition-lib.pc @ONLY)

install(FILES ${CMAKE_BINARY_DIR}/addition-lib.pc DESTINATION lib/pkgconfig)
