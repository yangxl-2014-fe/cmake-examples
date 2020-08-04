cmake_minimum_required(VERSION 3.5)

# Set the project name
project (05_boost_unit_test)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)


# find a boost install with the libraries unit_test_framework
find_package(Boost 1.46.1 REQUIRED COMPONENTS unit_test_framework)

# Add an library for the example classes
add_library(example_boost_unit_test
    Reverse.cpp
    Palindrome.cpp
)

target_include_directories(example_boost_unit_test
    PUBLIC
        ${CMAKE_CURRENT_SOURCE_DIR}
)

target_link_libraries(example_boost_unit_test
    PUBLIC
        Boost::boost
)

#############################################
# Unit tests

# enable CTest testing
enable_testing()

# Add a testing executable
add_executable(05_unit_tests unit_tests.cpp)

target_link_libraries(05_unit_tests
    example_boost_unit_test
    Boost::unit_test_framework
)

target_compile_definitions(05_unit_tests
    PRIVATE
        BOOST_TEST_DYN_LINK
)

add_test(test_all_boost 05_unit_tests)