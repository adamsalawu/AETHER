cmake_minimum_required(VERSION 3.21)
project(D1VITuner VERSION 1.0.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)

find_package(Qt6 6.4 REQUIRED COMPONENTS Widgets)

qt_add_executable(D1VITuner WIN32
    src/main.cpp
)

target_link_libraries(D1VITuner PRIVATE Qt6::Widgets PowrProf Psapi Advapi32 Ole32 Dxgi Pdh)
target_compile_definitions(D1VITuner PRIVATE UNICODE _UNICODE WIN32_LEAN_AND_MEAN NOMINMAX)
if(MSVC)
    target_compile_options(D1VITuner PRIVATE /W4 /permissive- /utf-8)
endif()
