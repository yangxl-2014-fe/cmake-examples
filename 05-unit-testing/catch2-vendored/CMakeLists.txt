cmake_minimum_required(VERSION 3.5)

# Set the project name
project (05_catch2_unit_test)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)


set(CMAKE_CXX_STANDARD 11)

# add the CMakeFile that defines catch2
add_subdirectory(3rd_party/catch2)

# Add an library for the example classes
add_library(example_unit_test
    Reverse.cpp
    Palindrome.cpp
)


#############################################
# Unit tests

# enable CTest testing
enable_testing()

# Add a testing executable
add_executable(05_catch2_unit_tests unit_tests.cpp)

target_link_libraries(05_catch2_unit_tests
    example_unit_test
    Catch2::Test
)

add_test(test_all_catch2 05_catch2_unit_tests)