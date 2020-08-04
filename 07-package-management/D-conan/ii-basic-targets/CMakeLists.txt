cmake_minimum_required(VERSION 3.5)
project (07_ii_conan_third_party_include)

set(CMAKE_CXX_STANDARD 11)

# Included the conan build information
# include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
include($ENV{HOME}/conanbuildinfo.cmake)
conan_basic_setup(TARGETS)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)

# Add an executable
add_executable(07_ii_third_party_include main.cpp)

# link against the fmt target supplied by conan
target_link_libraries(07_ii_third_party_include
    PRIVATE
        CONAN_PKG::fmt
)