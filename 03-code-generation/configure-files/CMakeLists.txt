cmake_minimum_required(VERSION 3.5)

# Set the project name
project (03_cf_example)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)

# set a project version
set (cf_example_VERSION_MAJOR 0)
set (cf_example_VERSION_MINOR 2)
set (cf_example_VERSION_PATCH 1)
set (cf_example_VERSION "${cf_example_VERSION_MAJOR}.${cf_example_VERSION_MINOR}.${cf_example_VERSION_PATCH}")

# Call configure files on ver.h.in to set the version.
# Uses the standard ${VARIABLE} syntax in the file
configure_file(ver.h.in ${PROJECT_BINARY_DIR}/ver.h)

# configure the path.h.in file.
# This file can only use the @VARIABLE@ syntax in the file
configure_file(path.h.in ${PROJECT_BINARY_DIR}/path.h @ONLY)

# Add an executable
add_executable(03_cf_example
    main.cpp
)

# include the directory with the new files
target_include_directories( 03_cf_example
    PUBLIC
        # ${CMAKE_BINARY_DIR}
        ${PROJECT_BINARY_DIR}
)