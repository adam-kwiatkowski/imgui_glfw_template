cmake_minimum_required(VERSION 3.28)
project(imgui_glfw_template)

set(CMAKE_CXX_STANDARD 17)

add_subdirectory(external/glfw)
find_package(OpenGL REQUIRED)

set(IMGUI_DIR external/imgui)
include_directories(${IMGUI_DIR} ${IMGUI_DIR}/backends)

set(IMGUI_SOURCES
        ${IMGUI_DIR}/backends/imgui_impl_glfw.cpp
        ${IMGUI_DIR}/backends/imgui_impl_opengl3.cpp
        ${IMGUI_DIR}/imgui.cpp
        ${IMGUI_DIR}/imgui_draw.cpp
        ${IMGUI_DIR}/imgui_demo.cpp
        ${IMGUI_DIR}/imgui_tables.cpp
        ${IMGUI_DIR}/imgui_widgets.cpp
)

set(sources
    main.cpp
    ${IMGUI_SOURCES}
)

add_executable(imgui_glfw_template ${sources})
target_link_libraries(${CMAKE_PROJECT_NAME} glfw OpenGL::GL)