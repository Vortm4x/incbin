cmake_minimum_required(VERSION 3.21)
project(incbin LANGUAGES C)

set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED ON)

set(PROJECT_ROOT ${CMAKE_CURRENT_LIST_DIR})

set(PROJECT_SOURCES
    ${PROJECT_ROOT}/incbin.c
    ${PROJECT_ROOT}/include/incbin.h
)

add_library(
    ${PROJECT_NAME} SHARED
    ${PROJECT_SOURCES}
)

add_library(
    ${PROJECT_NAME}::${PROJECT_NAME} 
    ALIAS ${PROJECT_NAME}
)

add_library(
    ${PROJECT_NAME}_static STATIC 
    ${PROJECT_SOURCES}
)

add_library(
    ${PROJECT_NAME}::${PROJECT_NAME}_static
    ALIAS ${PROJECT_NAME}_static
)

target_include_directories(
    ${PROJECT_NAME} PUBLIC ${PROJECT_ROOT}/include
)

target_include_directories(
    ${PROJECT_NAME}_static PUBLIC ${PROJECT_ROOT}/include
)
