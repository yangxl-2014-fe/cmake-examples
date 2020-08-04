# Set the project name
project (04_cppcheck_subproject2)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)

# Create a sources variable with a link to all cpp files to compile
set(SOURCES
    main2.cpp
)

# include the file with the function then call the macro
include(${CMAKE_SOURCE_DIR}/cmake/analysis.cmake)
add_analysis(${PROJECT_NAME} SOURCES)

# Add an executable with the above sources
add_executable(${PROJECT_NAME} ${SOURCES})