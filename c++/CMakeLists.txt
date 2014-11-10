cmake_minimum_required(VERSION 2.8)

project(sodium)


set(SODIUM_BASE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/sodium)

file(GLOB_RECURSE
    SODIUM_INCLUDE_FILES
    ${SODIUM_BASE_DIR}/*.h
)

file(GLOB_RECURSE
    SODIUM_SOURCE_FILES
    ${SODIUM_BASE_DIR}/*.cpp
)

include_directories(${CMAKE_CURRENT_SOURCE_DIR})

set(ALL_SOURCES ${SODIUM_INCLUDE_FILES} ${SODIUM_SOURCE_FILES})
        
add_library(sodium SHARED ${ALL_SOURCES})


