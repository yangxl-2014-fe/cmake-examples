cmake_minimum_required(VERSION 3.5)

project(01C_hello_library)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)

############################################################
# Create a library
############################################################

#Generate the static library from the library sources
add_library(01C_hello_library STATIC 
    src/Hello.cpp
)

target_include_directories(01C_hello_library
    PUBLIC 
        ${PROJECT_SOURCE_DIR}/include
)


############################################################
# Create an executable
############################################################

# Add an executable with the above sources
add_executable(01C_hello_binary 
    src/main.cpp
)

# link the new hello_library target with the hello_binary target
target_link_libraries( 01C_hello_binary
    PRIVATE 
        01C_hello_library
)