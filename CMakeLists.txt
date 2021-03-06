cmake_minimum_required(VERSION 3.14)

project(Configuration VERSION 0.1 LANGUAGES CXX)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

IF (APPLE)
set(CMAKE_PREFIX_PATH ${CMAKE_PREFIX_PATH} "/usr/local/opt/qt5/lib/cmake")
ENDIF()


set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(QT NAMES Qt6 Qt5 COMPONENTS Core Quick WebSockets Network NetLinguistTools REQUIRED)
find_package(Qt${QT_VERSION_MAJOR} COMPONENTS Core Quick WebSockets Network LinguistTools REQUIRED)


set(PROJECT_SOURCES
        src/main.cpp
)


add_executable(Configuration
    ${PROJECT_SOURCES}
)

### add extra qt library
target_link_libraries(Configuration
    PRIVATE Qt${QT_VERSION_MAJOR}::Core Qt${QT_VERSION_MAJOR}::Quick Qt${QT_VERSION_MAJOR}::WebSockets Qt${QT_VERSION_MAJOR}::Network)
