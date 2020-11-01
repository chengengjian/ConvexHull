cmake_minimum_required(VERSION 3.1)

# Name the project
project(ConvexHullConstruction)

if(NOT MSVC)
  set(CMAKE_CXX_FLAGS "-fpermissive -std=c++11")
endif()

# Find DartLib
find_package(DartLib REQUIRED HINTS "${CMAKE_SOURCE_DIR}/3rdparty")
if(NOT DartLib_FOUND)
    message(FATAL_ERROR "MeshLib Not Found!")
endif()

# Find OpenGL and GLUT
if(MSVC)
  find_package(freeglut REQUIRED HINTS "${CMAKE_SOURCE_DIR}/3rdparty")
  if(NOT freeglut_FOUND)
    message(FATAL_ERROR "freeglut Not Found!")
  endif()
else(MSVC)
  find_package(OpenGL REQUIRED)
  find_package(GLUT REQUIRED)
endif()

# Add module
add_subdirectory("convex_hull")
