cmake_minimum_required (VERSION 3.0.0)

project (CMake_Examples VERSION 0.1.0)

message(NOTICE "  -> CMAKE_MODULE_PATH: ${CMAKE_MODULE_PATH}")
message(NOTICE "  -> CMAKE_BINARY_DIR:  ${CMAKE_BINARY_DIR}")

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

set(CMAKE_BUILD_TYPE Release)

add_subdirectory (01-basic)
add_subdirectory (02-sub-projects)
add_subdirectory (03-code-generation)
add_subdirectory (04-static-analysis)
add_subdirectory (05-unit-testing)
add_subdirectory (06-installer)
add_subdirectory (07-package-management)