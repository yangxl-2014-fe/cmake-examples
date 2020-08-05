cmake_minimum_required(VERSION 3.5)

# Set the project name
project (05_google_test_example)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)

# Add an library for the example classes
add_library(example_google_test 
    Reverse.cpp
    Palindrome.cpp
)


#############################################
# Unit tests

add_subdirectory(3rd_party/google-test)

# enable CTest testing
enable_testing()

# Add a testing executable
add_executable(05_googletest_unit_tests unit_tests.cpp)

target_link_libraries(05_googletest_unit_tests
    example_google_test
    GTest::GTest 
    GTest::Main
)

add_test(test_all_google 05_googletest_unit_tests)