cmake_minimum_required(VERSION 3.5)
project(project CXX)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

#raylib
add_subdirectory(libs/raylib)

#imgui
set(IMGUI_SOURCES 
"libs/imgui/imgui_demo.cpp" 
"libs/imgui/imgui_draw.cpp"
"libs/imgui/imgui_tables.cpp"
"libs/imgui/imgui_widgets.cpp"
"libs/imgui/imgui.cpp"
)
set(IMGUI_INCLUDE "libs/imgui/")
set(RLIMGUI_SOURCES "libs/rlimgui/rlImGui.cpp")
set(RLIMGUI_INCLUDE "libs/rlimgui/")

# game source files
file(GLOB_RECURSE PROJECT_SOURCES "${CMAKE_CURRENT_LIST_DIR}/src/**.cpp")
set(PROJECT_INCLUDE "${CMAKE_CURRENT_LIST_DIR}/src/")

# Declaring our executable
add_executable(${PROJECT_NAME})
target_sources(${PROJECT_NAME} PRIVATE ${PROJECT_SOURCES} ${IMGUI_SOURCES} ${RLIMGUI_SOURCES})
target_include_directories(${PROJECT_NAME} PRIVATE ${PROJECT_INCLUDE} ${IMGUI_INCLUDE} ${RLIMGUI_INCLUDE})
target_link_libraries(${PROJECT_NAME} PRIVATE raylib)