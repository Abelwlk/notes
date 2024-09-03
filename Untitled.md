正常

![image-20240521161137724](D:\workspace\notes\images\image-20240521161137724.png)

异常

![image-20240521161112527](D:\workspace\notes\images\image-20240521161112527.png)

```cmake
cmake_minimum_required(VERSION 3.5)

project(Auth2 VERSION 1.0 LANGUAGES CXX)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/lib)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/lib)

option(USE_PRODUCT_SERVER "是否使用正式服地址" OFF)

include_directories(${PROJECT_SOURCE_DIR}/include)
include_directories(${PROJECT_SOURCE_DIR}/3rdparty)

add_library(${PROJECT_NAME} SHARED
    src/auth2.cpp
    src/auth_udisk.cpp
    src/product_registration.cpp
    src/aes_quick.cpp
    3rdparty/md5.cpp
    3rdparty/AES.cpp
    3rdparty/base64.cpp
)

if(WIN32)
  target_link_libraries(${PROJECT_NAME} ws2_32)
endif()

#根据动态添加宏
target_compile_definitions(${PROJECT_NAME} PUBLIC 
    $<$<BOOL:${USE_PRODUCT_SERVER}>:USE_PRODUCT_SERVER>
    $<${WIN32}:_WIN32_WINNT=0x0A00>
    DLL_EXPORT_ENABLE
)

# 复制头文件到生成目录
add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
    "${PROJECT_SOURCE_DIR}/include/auth2.h"
    "${PROJECT_SOURCE_DIR}/include/aes_quick.h"
    $<TARGET_FILE_DIR:${PROJECT_NAME}>
)


```

