# The same as K-imported-targets/CMakeLists.txt
cmake_minimum_required(VERSION 3.5)

# Set the project name
project (01H_third_party_include)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)


# find a boost install with the libraries filesystem and system
find_package(Boost 1.46.1 REQUIRED COMPONENTS filesystem system)

# check if boost was found
if(Boost_FOUND)
    message ("boost found")
else()
    message (FATAL_ERROR "Cannot find Boost")
endif()

# Add an executable
add_executable(01H_third_party_include main.cpp)

# link against the boost libraries
target_link_libraries( 01H_third_party_include
    PRIVATE
        Boost::filesystem
)