# Set the minimum version of CMake that can be used
# To find the cmake version run
# $ cmake --version
cmake_minimum_required(VERSION 3.1)

# Set the project name
project (01Lii_hello_cpp11)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)

# set the C++ standard to C++ 11
set(CMAKE_CXX_STANDARD 11)

# Add an executable
add_executable(01Lii_hello_cpp11 main.cpp)