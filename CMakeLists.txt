cmake_minimum_required(VERSION 3.10)
project(WarehouseApp)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

if(MSVC)
    add_compile_options(/W4)
else()
    add_compile_options(-Wall -Wextra)
endif()

include_directories(src)
add_executable(WarehouseApp
    src/main.cpp
    src/Product.cpp
    src/Warehouse.cpp
    src/FileIO.cpp
    src/Menu.cpp
)

# Линковка std::filesystem для GCC <= 8
if(NOT MSVC AND CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
    target_link_libraries(WarehouseApp stdc++fs)
endif()