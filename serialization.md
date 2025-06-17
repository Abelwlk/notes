# Serialization Library

## 简介

Serialization 是一个基于 RTTR（Run-Time Type Reflection）的序列化库，支持将C++对象转换为 JSON 和 XML 格式的字符串，并能够从这些格式的字符串反序列化为对象。

## 功能特性

- **JSON 序列化与反序列化**：支持将对象转换为 JSON 字符串，并从 JSON 字符串解析为对象。
- **XML 序列化与反序列化**：支持将对象转换为 XML 字符串，并从 XML 字符串解析为对象。
- **RTTR 集成**：利用 RTTR 提供的反射能力，自动处理对象的属性序列化。
- **支持多种数据类型**：
  - 算术类型（如 `int`, `float`, `double` 等）
  - 枚举类型
  - 字符串
  - 容器类型（如 `std::vector`, `std::map` 等）
  - 自定义类

## 依赖项

- **[RTTR](https://github.com/rttrorg/rttr)**：用于运行时反射。
  - 下载源代码&编译&安装到系统环境，参考项目[安装教程](https://www.rttr.org/doc/master/building_install_page.html)。
- **[nlohmann/json](nlohmann/json)**：用于 JSON 的解析和生成（仅 JSON 模块需要）。
  - head-only库，已集成到项目中。
- **[tinyxml2](https://github.com/leethomason/tinyxml2)**：用于 XML 的解析和生成（仅 XML 模块需要）。
  - head-only库，已集成到项目中。



## 使用方法

### 1. 引入头文件

在使用 serialization 库之前，请确保引入以下头文件：

```c++
#include "serialization/serialize_json.h"
#include "serialization/serialize_xml.h"
```

### 2. JSON 序列化与反序列化

#### 序列化

将支持 RTTR 反射的对象转换为 JSON 字符串：

```c++
MyClass obj = ...; // 初始化对象
std::string json_str = serialization::to_json(obj);
```

#### 反序列化

从 JSON 字符串解析为支持 RTTR 反射的对象：

```c++
MyClass new_obj; // 初始化对象实例
std::string json_str = "..."; // JSON 字符串
bool success = serialization::from_json(new_obj, json_str);
```

### 3. XML 序列化与反序列化

#### 序列化

将支持 RTTR 反射的对象转换为 XML 字符串：

```c++
MyClass obj = ...; // 初始化对象
std::string xml_str = serialization::to_xml(obj);
```

#### 反序列化

从 XML 字符串解析为支持 RTTR 反射的对象：

```c++
MyClass new_obj = ...; // 初始化对象实例
std::string xml_str = "..."; // XML 字符串
bool success = serialization::from_xml(obj, xml_str);
```

### 4. 注意事项

- 对象必须注册到 RTTR 中，才能被正确序列化和反序列化。例如：

    ```c++
    RTTR_REGISTRATION
    {
        rttr::registration::class_<MyClass>("MyClass")
            .constructor<>()(rttr::policy::ctor::as_object) // policy: 反射调用构造时创建对象在栈上
            .property("myProperty", &MyClass::myProperty)
            .property("anotherProperty", &MyClass::anotherProperty);
    }
    ```

- 如果某些属性不需要参与序列化，可以在注册时添加 `"NO_SERIALIZE"` 元数据：

    ```c++
    RTTR_REGISTRATION
    {
        rttr::registration::class_<MyClass>("MyClass")
            .constructor<>()(rttr::policy::ctor::as_object) // policy: 反射调用构造时创建对象在栈上
            .property("myProperty", &MyClass::myProperty)
            .property("anotherProperty", &MyClass::anotherProperty)
                .add_metadata("NO_SERIALIZE", true);
    }
    ```

- 枚举注册时，可配置映射序列化时的字符串

  ```c++
  rttr::registration::enumeration<TestEnum>("TestEnum")(
      rttr::value("Value1", TestEnum::Value1),
      rttr::value("Value2", TestEnum::Value2),
      rttr::value("Value3", TestEnum::Value3));
  ```

  

## 示例代码

### JSON 示例

```c++
#include "serialization/serialize_json.h"

struct MyClass {
    int myInt;
    std::string myString;
};

RTTR_REGISTRATION
{
    rttr::registration::class_<MyClass>("MyClass")
        .property("myInt", &MyClass::myInt)
        .property("myString", &MyClass::myString);
}

int main() {
    MyClass obj = {42, "Hello"};
    std::string json_str = serialization::to_json(obj);
    std::cout << "Serialized JSON: " << json_str << std::endl;

    MyClass new_obj;
    bool success = serialization::from_json(new_obj, json_str);
    if (success) {
        std::cout << "Deserialized JSON: myInt=" << new_obj.myInt 
                  << ", myString=" << new_obj.myString << std::endl;
    }
    return 0;
}
```

### XML 示例

```c++
#include "serialization/serialize_xml.h"

struct MyClass {
    int myInt;
    std::string myString;
};

RTTR_REGISTRATION
{
    rttr::registration::class_<MyClass>("MyClass")
        .property("myInt", &MyClass::myInt)
        .property("myString", &MyClass::myString);
}

int main() {
    MyClass obj = {42, "Hello"};
    std::string xml_str = serialization::to_xml(obj);
    std::cout << "Serialized XML: " << xml_str << std::endl;

    MyClass new_obj;
    bool success = serialization::from_xml(new_obj, xml_str);
    if (success) {
        std::cout << "Deserialized XML: myInt=" << new_obj.myInt 
                  << ", myString=" << new_obj.myString << std::endl;
    }
    return 0;
}
```
