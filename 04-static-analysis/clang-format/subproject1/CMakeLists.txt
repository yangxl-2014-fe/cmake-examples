# Set the project name
project (04_format_subproject1)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)

# Add an executable with the above sources
add_executable(${PROJECT_NAME} main1.cpp)