cmake_minimum_required (VERSION 3.5)

project(04_cppcheck_cc_analysis)

# Have cmake create a compile database
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# Add a custom CMake Modules directory
set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake/modules
                      ${CMAKE_MODULE_PATH})

# include(${CMAKE_CURRENT_SOURCE_DIR}/cmake/modules/FindCppCheck.cmake)
# find the cppcheck binary
find_package(CppCheck)

# Add sub directories
add_subdirectory(subproject1)
add_subdirectory(subproject2)
