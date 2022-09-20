cmake_minimum_required(VERSION 3.8)

file(READ "version.txt" ver)
string(REGEX MATCH "VERSION_MAJOR ([0-9]*)" _ ${ver})
set(ver_major ${CMAKE_MATCH_1})

string(REGEX MATCH "VERSION_MINOR ([0-9]*)" _ ${ver})
set(ver_minor ${CMAKE_MATCH_1})

string(REGEX MATCH "VERSION_PATCH ([0-9]*)" _ ${ver})
set(ver_patch ${CMAKE_MATCH_1})

string(REGEX MATCH "VERSION_TWEAK ([0-9]*)" _ ${ver})
set(ver_tweak ${CMAKE_MATCH_1})

message("version: ${ver_major}.${ver_minor}.${ver_patch}")
set(version "${ver_major}.${ver_minor}.${ver_patch}.${ver_tweak}")

project(sampleApp VERSION ${version} LANGUAGES CXX)

set(PATH_TO_SOURCES ${CMAKE_CURRENT_SOURCE_DIR})

include_directories(${CMAKE_BINARY_DIR})

configure_file (
    "${PATH_TO_SOURCES}/version.h.in"
    "${CMAKE_BINARY_DIR}/version.h"
)

add_executable(${PROJECT_NAME} main.cpp)

add_subdirectory(second_app)