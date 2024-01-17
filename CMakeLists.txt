# This line is required for CMake projects, it determines what version of CMake you're defualting to
cmake_minimum_required(VERSION 3.22)

# This line allows you to access some env variables later on
project(AudioPluginTemplate)

# This line allows you to access the latest CMake standards
set(CMAKE_CXX_STANDARD 23)

set(LIB_DIR ${CMAKE_CURRENT_SOURCE_DIR}/libs)
include(cmake/cpm.cmake)