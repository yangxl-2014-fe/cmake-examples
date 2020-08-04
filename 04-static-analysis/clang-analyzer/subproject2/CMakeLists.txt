# Set the project name
project (04_analyzer_subproject2)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)

# Add an executable with the above sources
add_executable(${PROJECT_NAME} main2.cpp)