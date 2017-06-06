cmake_minimum_required(VERSION 3.0.2)
project(tiny-aes)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
SET(CMAKE_DEFAULT_STARTUP_PROJECT tiny-aes)

SET(GCC_COVERAGE_COMPILE_FLAGS "ECB=1")
SET(GCC_COVERAGE_LINK_FLAGS "")

file(GLOB SOURCES "aes.c")

SET( CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} ${GCC_COVERAGE_COMPILE_FLAGS}" )
SET( CMAKE_EXE_LINKER_FLAGS  "${CMAKE_EXE_LINKER_FLAGS} ${GCC_COVERAGE_LINK_FLAGS}" )

# vscode cmake tools
include(CMakeToolsHelpers OPTIONAL)

# lib
add_library(aes STATIC ${SOURCES})

# exe
add_executable(tiny-aes test.c)
target_link_libraries(tiny-aes aes)

