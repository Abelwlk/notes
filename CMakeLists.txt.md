```cmake
cmake_minimum_required(VERSION 3.25)
project(ch3_2LessWidgetPro)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

set(CMAKE_PREFIX_PATH "C:/Qt/5.15.2/mingw_64")

find_package(Qt5 COMPONENTS
        Core
        Gui
        Widgets
        REQUIRED)

file(GLOB H_FILE *.h)
file(GLOB SRC_FILE *.cpp)
file(GLOB UI_FILE *.ui)
file(GLOB QRC_FILE *.qrc)

add_executable(ch3_2LessWidgetPro
        ${H_FILE}
        ${SRC_FILE}
        ${UI_FILE}
        ${QRC_FILE})

target_link_libraries(ch3_2LessWidgetPro
        Qt::Core
        Qt::Gui
        Qt::Widgets
        )

```