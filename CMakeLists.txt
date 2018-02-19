cmake_minimum_required(VERSION 3.2)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

include_directories(
        src/common)
aux_source_directory(
        src/common
        COMMON_SOURCE_FILES)
add_library(
        common
        STATIC
        ${COMMON_SOURCE_FILES})
target_link_libraries(
        common
        gps
        pthread
        ncurses)

aux_source_directory(src GPSD_SOURCE_FILES)
add_executable(gpsdrun ${GPSD_SOURCE_FILES})
target_link_libraries(gpsdrun common)
