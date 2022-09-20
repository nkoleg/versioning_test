cmake_minimum_required(VERSION 3.8)

project(secondApp VERSION 3.2.1.43 LANGUAGES CXX)

set(PATH_TO_SOURCES ${CMAKE_CURRENT_SOURCE_DIR})

include_directories(${CMAKE_BINARY_DIR})

configure_file (
    "${PATH_TO_SOURCES}/version.h.in"
    "${CMAKE_BINARY_DIR}/version_second.h"
)

add_executable(${PROJECT_NAME} second.cpp)
