cmake_minimum_required(VERSION 3.8)
project(opengl)

set(CMAKE_CXX_STANDARD 14)
set(SOURCE_FILES main.cpp)
add_executable(opengl ${SOURCE_FILES})

# Running OpenGL on Ubuntu with CLion
# Add this to your Cmake Lists
# @author : adwitiya (github.com/adwitiya)
# make sure you run "sudo apt-get install freeglut3 freeglut3-dev libglew1.5 libglew1.5-dev libglu1-mesa libglu1-mesa-dev libgl1-mesa-glx libgl1-mesa-dev"
# to install all dependencies.
#########################################################
# FIND GLUT
#########################################################
find_package(GLUT REQUIRED)
include_directories(${GLUT_INCLUDE_DIRS})
link_directories(${GLUT_LIBRARY_DIRS})
add_definitions(${GLUT_DEFINITIONS})
if(NOT GLUT_FOUND)
    message(ERROR " GLUT not found!")
endif(NOT GLUT_FOUND)
#########################################################
# FIND OPENGL
#########################################################
find_package(OpenGL REQUIRED)
include_directories(${OpenGL_INCLUDE_DIRS})
link_directories(${OpenGL_LIBRARY_DIRS})
add_definitions(${OpenGL_DEFINITIONS})
if(NOT OPENGL_FOUND)
    message(ERROR " OPENGL not found!")
endif(NOT OPENGL_FOUND)

#########################################################
# FIND GLEW
#########################################################
find_library(GLEW_LIBRARY GLEW)
if (NOT GLEW_FOUND)
    message(ERROR " GLEW not found!")
endif(NOT GLEW_FOUND)

# change your project name from opengl to your given name
target_link_libraries(opengl ${OPENGL_LIBRARIES} ${GLUT_LIBRARY} ${GLEW_LIBRARY})