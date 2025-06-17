### Auth2

#### 概述

提供U盘在线认证、装机注册设备编号上传、装机注册注册码本地校验、生成动态码、验证码等接口实现。

额外附带执行终端命令函数、[AES](https://github.com/SergeyBel/AES)加密算法封装与[base64](https://renenyffenegger.ch/notes/development/Base64/Encoding-and-decoding-base-64-with-cpp)、[json](https://github.com/nlohmann/json)、[http](https://github.com/yhirose/cpp-httplib)、[MD5](https://github.com/yaoyao-cn/md5)等第三方优秀开源库。

#### 编译&安装

##### 工具链要求

- gcc8-gcc13（没有在其他版本上编译

- CMake 3.5+
- git

##### 编译

1. 拉取代码

   ```bash
   git clone git@gitlab.medlander.com:software/BaseLibrary/auth2.git
   ```

2. 编译

   ```shell
   cd Auth2
   mkdir build
   cd build & cmake ..
   ```

##### 安装

编译成功后，复制lib目录下相关头文件&库文件到项目中，引用头文件&链接库文件。

#### 项目结构

```bash
AUTH2
│   .clang-format	#clang格式化文件
│   .gitignore
│   CMakeLists.txt
│   
├───.vscode
│       c_cpp_properties.json
│       settings.json
│
├───3rdparty #三方库
│   ├───include
│   │       AES.h
│   │       base64.h
│   │       httplib.h
│   │       json.hpp
│   │       md5.h
│   │
│   └───src
│           AES.cpp
│           base64.cpp
│           md5.cpp
│
├───include #项目头文件
│       aes_quick.h #aes封装
│       auth2.h #对外统一接口头文件
│       auth_udisk.h #U盘校验
│       product_registration.h #装机注册相关
│
├───lib #编译生成
│       AES.h
│       aes_quick.h
│       auth2.h
│       libAuth2.dll
│       libAuth2.dll.a
│
├───src #对头文件的实现
│       aes_quick.cpp
│       auth2.cpp
│       auth_udisk.cpp
│       product_registration.cpp
│
└───test
        main.cpp
```

#### 文档

注释非常详细，见注释。