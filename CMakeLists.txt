cmake_minimum_required(VERSION 3.11)

project(nGL)

#creating a static library
add_library(${PROJECT_NAME} gl.cpp
    fastmath.cpp
    gldrawarray.cpp
    texturetools.cpp
    fastmath.h
    fix.h
    gl.h
    glconfig.h
    gldrawarray.h
    texturetools.h
    triangle.inc.h
)

include(FindPkgConfig)
pkg_search_module(SDL REQUIRED sdl)

target_include_directories(${PROJECT_NAME} PRIVATE ${SDL_INCLUDE_DIRS})

target_link_libraries(${PROJECT_NAME} PRIVATE
    ${SDL_LIBRARIES}
    pspgu
    pspge
    pspdebug
    pspdisplay
    pspkernel
    m
    pspsdk
)

# Create an EBOOT.PBP file

