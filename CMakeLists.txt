cmake_minimum_required(VERSION 3.1)
project(triangle)

add_library(triangle STATIC triangle.cpp)
target_compile_definitions(triangle PRIVATE -DTRILIBRARY -DANSI_DECLARATORS)
if(WIN32)
   target_compile_definitions(triangle PRIVATE -DNO_TIMER)
endif()

if(UNIX)
    target_compile_options(triangle PRIVATE -fPIC -fvisibility=hidden)
endif(UNIX)

INSTALL(TARGETS triangle
    LIBRARY DESTINATION lib
    ARCHIVE DESTINATION lib
    )
INSTALL(FILES triangle.h DESTINATION include)
