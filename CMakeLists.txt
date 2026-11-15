cmake_minimum_required(VERSION 3.20)

project(PIPL
    VERSION 0.1.0
    DESCRIPTION "Parallel Image Processing Lab"
    LANGUAGES CXX
)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

add_executable(pipl
    src/main.cpp
)

target_include_directories(pipl
    PRIVATE
        ${PROJECT_SOURCE_DIR}/include
)

if(CMAKE_CXX_COMPILER_ID MATCHES "GNU|Clang")
    target_compile_options(pipl PRIVATE
        -Wall
        -Wextra
        -Wpedantic
    )
endif()
