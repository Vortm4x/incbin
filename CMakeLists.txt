cmake_minimum_required(VERSION 3.21)
project(incbin LANGUAGES C)

set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED ON)

set(PROJECT_ROOT ${CMAKE_CURRENT_LIST_DIR})

add_library(${PROJECT_NAME} INTERFACE)

target_include_directories(
    ${PROJECT_NAME} INTERFACE 
    ${PROJECT_ROOT}/include
)


set(INCBIN_TOOL ${PROJECT_NAME}_tool)

add_executable(
    ${INCBIN_TOOL}
    ${PROJECT_ROOT}/incbin.c
)
