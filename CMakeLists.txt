cmake_minimum_required(VERSION 3.10)
project(OpenGLExample)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# OpenGL and GLFW
find_package(OpenGL REQUIRED)

set(HOMEBREW_PREFIX /opt/homebrew)
find_path(GLFW_INCLUDE_DIR GLFW/glfw3.h PATHS ${HOMEBREW_PREFIX}/include)
find_library(GLFW_LIBRARY glfw PATHS ${HOMEBREW_PREFIX}/lib)

# Add include directories for GLAD
include_directories(${GLFW_INCLUDE_DIR} ${CMAKE_SOURCE_DIR}/include)

# Add your source files (include glad.c)
add_executable(main
    src/main.cpp
    src/glad.c
)

target_link_libraries(main
    ${OPENGL_LIBRARIES}
    ${GLFW_LIBRARY}
)

