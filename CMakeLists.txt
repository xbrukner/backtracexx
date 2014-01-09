project(backtracexx)
cmake_minimum_required(VERSION 2.8)

# ADDR2LINE support for line numbers
find_program(ADDR2LINE addr2line PATHS)
IF(ADDR2LINE)
        add_definitions(-DADDR2LINE=${ADDR2LINE})
ENDIF(ADDR2LINE)

add_library(backtracexx STATIC backtracexx.cpp)

IF(UNIX)
        target_link_libraries(backtracexx dl)
ENDIF(UNIX)
