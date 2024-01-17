# This line is required for CMake projects, it determines what version of CMake you're defualting to
cmake_minimum_required(VERSION 3.22)

# This line allows you to access some env variables later on
project(AudioPluginTemplate)

# This line allows you to access the latest CMake standards
set(CMAKE_CXX_STANDARD 23)

# This line determines the output of your cmake function
set(LIB_DIR ${CMAKE_CURRENT_SOURCE_DIR}/libs)

# This line runs the declared cmake file in order to generate file creation 
include(cmake/cpm.cmake)

# This line utilizes the CPM Package manager, that was downloaded in the previous line, to install 3rd party dependencies
CPMAddPackage(
    NAME JUCE
    GITHUB_REPOSITORY juce-framework/JUCE
    # if the git tag has a tiny 'v', use it, if not then don't. In this case it does not have a tiny 'v'
    GIT_TAG 7.0.9
    VERSION 7.0.9
    SOURCE_DIR ${LIB_DIR}/juce
)

if (MSVC)
    add_compile_options(/Wall /WX)
else()
    add_compile_options(-Wall -Wextra -Wpedantic)
endif()

add_subdirectory(plugin)