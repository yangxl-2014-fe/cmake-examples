cmake_minimum_required(VERSION 3.5)
project (07_conan_third_party_include)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)

set(CMAKE_CXX_STANDARD 11)

# Included the conan build information
include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup(TARGETS)

# Add an executable
add_executable(07_third_party_include main.cpp)

# link against the fmt target supplied by conan
target_link_libraries(07_third_party_include
    PRIVATE
        CONAN_PKG::fmt
)