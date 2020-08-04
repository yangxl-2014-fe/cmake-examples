cmake_minimum_required(VERSION 3.5)

# Set a default C++ compile flag
set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -DEX2" CACHE STRING "Set C++ Compiler Flags" FORCE)

# Set the project name
project (01G_compile_flags)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)

# Add an executable
add_executable(01G_cmake_examples_compile_flags main.cpp)

target_compile_definitions(01G_cmake_examples_compile_flags 
    PRIVATE EX3
)