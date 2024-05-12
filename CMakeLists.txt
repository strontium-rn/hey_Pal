cmake_minimum_required(VERSION 3.10)
project(heyPal)

# Set C++ standard
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Set the output directory for the executable
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin")

# Include directories
include_directories("${PROJECT_SOURCE_DIR}/source/headers")
include_directories("${PROJECT_SOURCE_DIR}/extern/imgui")

# Collect all source files
file(GLOB SOURCES "${PROJECT_SOURCE_DIR}/source/src/*.cpp")

# Collect Dear ImGui source files
file(GLOB IMGUI_SOURCES "${PROJECT_SOURCE_DIR}/extern/imgui/*.cpp")

# Create the executable
add_executable(heyPal ${SOURCES} ${IMGUI_SOURCES})

# Specify the include directories for the target
target_include_directories(heyPal PRIVATE "${PROJECT_SOURCE_DIR}/source/headers"
                                          "${PROJECT_SOURCE_DIR}/extern/imgui")
