cmake_minimum_required(VERSION 2.8)

project(sodium)

if(APPLE)
    set(CMAKE_CXX__FLAGS "-std=c++11 -stdlib=libc++")
    set(CMAKE_EXE_LINKER_FLAGS "-lc++ -stdlib=libc++")
endif()

set(SODIUM_BASE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/sodium)
set(CMAKE_INCLUDE_CURRENT_DIR ON)

find_package(Boost REQUIRED)

file(GLOB_RECURSE SODIUM_INCLUDE_FILES ${SODIUM_BASE_DIR}/*.h)

file(GLOB_RECURSE SODIUM_SOURCE_FILES ${SODIUM_BASE_DIR}/*.cpp)

file(COPY ${SODIUM_INCLUDE_FILES} DESTINATION ${CMAKE_CURRENT_BINARY_DIR}/include/sodium)

include_directories(${Boost_INCLUDE_DIR})

set(ALL_SOURCES ${SODIUM_INCLUDE_FILES} ${SODIUM_SOURCE_FILES})
        
add_library(sodium SHARED ${ALL_SOURCES})


