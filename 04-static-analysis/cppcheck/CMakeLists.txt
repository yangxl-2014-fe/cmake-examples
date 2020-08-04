cmake_minimum_required (VERSION 3.5)

project(04_cppcheck_analysis)

# Add a custom CMake Modules directory
set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake/modules
                      ${CMAKE_MODULE_PATH})

message(NOTICE "  ------> CMAKE_MODULE_PATH: ${CMAKE_MODULE_PATH}")

# include(${CMAKE_CURRENT_SOURCE_DIR}/cmake/modules/FindCppCheck.cmake)
# find the cppcheck binary
find_package(CppCheck)

# static analysis. Should be before adding subprojects
set (ALL_ANALYSIS_TARGETS)

# Add sub directories
add_subdirectory(subproject1)
add_subdirectory(subproject2)


# Add the "make analysis" target
if( CPPCHECK_FOUND )
    add_custom_target(04_cppcheck_analysis)
    ADD_DEPENDENCIES(04_cppcheck_analysis ${ALL_ANALYSIS_TARGETS})
    set_target_properties(04_cppcheck_analysis PROPERTIES EXCLUDE_FROM_ALL TRUE)
    message("analysis analysis targets are ${ALL_ANALYSIS_TARGETS}")
endif()
