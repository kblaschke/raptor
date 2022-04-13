cmake_minimum_required(VERSION 3.15)

project(Raptor
        LANGUAGES C CXX
        VERSION 1.0.0
        )

find_package(SDL2 NO_CMAKE_ENVIRONMENT_PATH NO_SYSTEM_ENVIRONMENT_PATH NO_CMAKE_SYSTEM_PATH REQUIRED)

add_compile_options(-Wall -Wpedantic)

if(CMAKE_SIZEOF_VOID_P EQUAL 8)
    # Use 32-to-64-bit pointer wrapper hack.
    add_compile_definitions(WRAP_GLB_PTR)
endif()

if(NOT MSVC)
    add_compile_definitions(_strdup=strdup)
endif()

add_subdirectory(include/textscreen/include)
add_subdirectory(src)
