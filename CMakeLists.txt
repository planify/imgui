# Minimum version of CMake that has all features required for this specific file.
cmake_minimum_required(VERSION 3.22)

# Create a static library that only has the sources this project requires.
add_library(imgui
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>/backends/imgui_impl_glfw.cpp
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>/backends/imgui_impl_opengl3.cpp
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>/imgui.cpp
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>/imgui_demo.cpp
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>/imgui_draw.cpp
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>/imgui_tables.cpp
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>/imgui_widgets.cpp
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>/misc/cpp/imgui_stdlib.cpp)

# ImGui does not have an include directory, so just make the entire source available for now.
target_include_directories(imgui PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>)

# ImGui depends on GLFW.
target_link_libraries(imgui PUBLIC glfw)
