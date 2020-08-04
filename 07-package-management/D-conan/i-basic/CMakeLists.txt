# ============================================================================ #
# References:
#   Open the Command Palette:
#     -> Ctrl + Shift + P
#          -> Python: Select Interpreter
#   sudo -H pip3 install -U conan
#   sudo -H pip3 install -U jinja2
#   https://github.com/microsoft/vscode-cmake-tools/issues/697#issuecomment-633001452
# ============================================================================ #

cmake_minimum_required(VERSION 3.5)
project (07_i_conan_third_party_include)

set(CMAKE_CXX_STANDARD 11)

message(NOTICE "  -> CMAKE_BINARY_DIR:         ${CMAKE_BINARY_DIR}")
message(NOTICE "  -> CMAKE_CURRENT_SOURCE_DIR: ${CMAKE_CURRENT_SOURCE_DIR}")

add_definitions("-std=c++11")

# https://github.com/microsoft/vscode-cmake-tools/issues/697#issuecomment-633001452
set(CONAN_INSTALL_CMD "conan install")
message("COMMAND: ${CONAN_INSTALL_CMD} ${CMAKE_CURRENT_SOURCE_DIR}")
execute_process(COMMAND bash -c "${CONAN_INSTALL_CMD} ${CMAKE_CURRENT_SOURCE_DIR}"
   RESULT_VARIABLE CMD_ERROR)

message( STATUS "CMD_ERROR:" ${CMD_ERROR})

message("CMAKE_BINARY_DIR is ${CMAKE_BINARY_DIR}")
message("CMAKE_CURRENT_BINARY_DIR is ${CMAKE_CURRENT_BINARY_DIR}")

# Included the conan build information
# include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)

message(NOTICE "ENV-HOME:   $ENV{HOME}")
include($ENV{HOME}/conanbuildinfo.cmake)
conan_basic_setup()

set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)

# Add an executable
add_executable(07_i_third_party_include main.cpp)

# link against the fmt target supplied by conan
target_link_libraries(07_i_third_party_include
    PRIVATE
        ${CONAN_LIBS}
)