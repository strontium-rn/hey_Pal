cmake_minimum_required(VERSION 3.10)
project(hey_Pal)

# Set C++ standard
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED True)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# Include directories
include_directories("${PROJECT_SOURCE_DIR}/headers")
include_directories("${PROJECT_SOURCE_DIR}/extern/imgui")
include_directories("${PROJECT_SOURCE_DIR}/extern/imgui/backends")

# Find required packages
find_package(glfw3 REQUIRED)

# Set OpenGL_GL_PREFERENCE to GLVND
set(OpenGL_GL_PREFERENCE GLVND)
find_package(OpenGL REQUIRED)

# Collect all source files
file(GLOB SOURCES "${PROJECT_SOURCE_DIR}/src/*.cpp")

# Collect Dear ImGui source files
file(GLOB IMGUI_SOURCES "${PROJECT_SOURCE_DIR}/extern/imgui/*.cpp"
     "${PROJECT_SOURCE_DIR}/extern/imgui/backends/imgui_impl_glfw.cpp"
     "${PROJECT_SOURCE_DIR}/extern/imgui/backends/imgui_impl_opengl3.cpp")

# Create the executable
add_executable(hey_Pal ${SOURCES} ${IMGUI_SOURCES})

# Specify the include directories for the target
target_include_directories(
  hey_Pal
  PRIVATE "${PROJECT_SOURCE_DIR}/headers" "${PROJECT_SOURCE_DIR}/extern/imgui"
          "${PROJECT_SOURCE_DIR}/extern/imgui/backends" "${GLFW_INCLUDE_DIRS}")

# Link libraries to the executable
target_link_libraries(hey_Pal PRIVATE glfw OpenGL::GL)
