cmake_minimum_required(VERSION 3.16)

project(hello)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

if (CMAKE_SYSTEM_NAME STREQUAL "Linux")
	set(ENV{QT_X11_NO_MITSHM} 1)
	set (CMAKE_PREFIX_PATH "/usr/lib/aarch-linux-gnu/cmake")
elseif (CMAKE_SYSTEM_NAME STREQUAL "Windows")
	set (CMAKE_PREFIX_PATH "C:/app/qt6/6.9.3/msvc2022_64/lib/cmake")
endif ()
find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Widgets)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Widgets)

set(PROJECT_SOURCES
        main.cpp
        mainwindow.cpp
        mainwindow.h
        mainwindow.ui
)

add_executable(hello ${PROJECT_SOURCES})

target_link_libraries(hello PRIVATE Qt${QT_VERSION_MAJOR}::Widgets)

