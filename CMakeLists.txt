cmake_minimum_required(VERSION 3.15)
project(imgui_dx11_example)

set(cmake_cxx_standard 17)

# path to imgui root
set(imgui_root ${CMAKE_SOURCE_DIR}/third_party/imgui)

# imgui + backend source files
set(imgui_sources
        ${imgui_root}/imgui.cpp
        ${imgui_root}/imgui_demo.cpp
        ${imgui_root}/imgui_draw.cpp
        ${imgui_root}/imgui_tables.cpp
        ${imgui_root}/imgui_widgets.cpp
        ${imgui_root}/backends/imgui_impl_dx11.cpp
        ${imgui_root}/backends/imgui_impl_win32.cpp
        GUI.cpp
        GUI.h
)

# add your main.cpp from root directory
add_executable(imgui_dx11_example
        main.cpp
        ${imgui_sources}
)

# include dirs
target_include_directories(imgui_dx11_example PRIVATE
        ${imgui_root}
        ${imgui_root}/backends
)

# windows + dx11 libraries
target_link_libraries(imgui_dx11_example
        d3d11 dxgi dxguid d3dcompiler dwmapi user32 gdi32
)
