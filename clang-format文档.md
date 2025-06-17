#### [Clang-Format Style Options — Clang 17.0.1 documentation (llvm.org)](https://releases.llvm.org/17.0.1/tools/clang/docs/ClangFormatStyleOptions.html)

##### AccessModifierOffset

- 访问修饰符的额外缩进或缩出，例如 `public:`

- ```c++
  AccessModifierOffset: -4
  IndentWidth: 4
  
  class Test {
  public:
  	/* data */
  private:
      /* data */
  };
  ```

##### AlignAfterOpenBracket

- 在左括号后水平对齐参数，适用于圆括号、尖括号和方括号

  - `Align`：将左括号中的参数对齐

    ```c++
    public:
        void print(int abcd, double bcde, long cdef, float wasd, std::string str1,
                   std::string str2);
    ```

  - `DontAlign`：不要对齐，而是使用`ContinuationIndentWidth`配置的缩进

    ```c++
    public:
        void print(int abcd, double bcde, long cdef, float wasd, std::string str1,
            std::string str2);
    ```

  - `AlwaysBreak`：如果参数不适合在一行中，则始终在左括号后换行

    ```c++
    public:
        void print(
            int abcd, double bcde, long cdef, float wasd, std::string str1,
            std::string str2);
    ```

  - `BlockIndent`：如果参数不适合在一行中，则始终在左括号后断开，右括号放在新行上

    ```c++
    public:
        void print(
            int abcd, double bcde, long cdef, float wasd, std::string str1,
            std::string str2
        );
    ```


##### AlignArrayOfStructures

- 如果不是`None`，对结构体数组初始化时对齐

  - `None`：不对齐数组初始化列

  - `Left`：对齐数组列并左对齐列

    ```c++
    struct test demo[] =
    {
        {56, 23,    "hello"},
        {-1, 93463, "world"},
        {7,  5,     "!!"   }
    };
    
    ```

  - `Right`：对齐数组列并右对齐列

    ```c++
    struct test demo[] =
    {
        {56,    23, "hello"},
        {-1, 93463, "world"},
        { 7,     5,    "!!"}
    };
    
    ```

##### AlignConsecutiveAssignments

- 连续赋值语句的对齐

  - **Enabled**：是否启用
    
    - `true`：
    
      ```c++
      int a            = 1;
      int somelongname = 2;
      double c         = 3;
      ```
    - `false`：
    
      ```c++
      int a = 1;
      int somelongname = 2;
      double c = 3;
      ```
  - **AcrossEmptyLines**：是否跨空行对齐
    
    - `true`：
    
      ```c++
      int a            = 1;
      int somelongname = 2;
      double c         = 3;
      
      int d            = 3;
      ```
    - `false`：
    
      ```c++
      int a            = 1;
      int somelongname = 2;
      double c         = 3;
      
      int d = 3;
      ```
  - **AcrossComments**：是否跨注释对齐
    
    - `true`：
    
      ```c++
      int d    = 3;
      /* A comment. */
      double e = 4;
      ```
    - `false`：
    
      ```c++
      int d = 3;
      /* A comment. */
      double e = 4;
      ```
  - **AlignCompound**：对齐赋值操作的操作符
    
    - `true`：
    
      ```c++
      a  &= 2;
      bbb = 2;
      ```
    - `false`：
    
      ```c++
      a &= 2;
      bbb = 2;
      ```
  - `PadOperators`：是否将短赋值运算符左填充到与长赋值运算符相同的长度，以便将所有赋值运算符放在左侧的右侧
    
    - `true`：
    
      ```c++
      a   >>= 2;
      bbb   = 2;
      ```
    - `false`：
    
      ```c++
      a >>= 2;
      bbb = 2;
      ```

##### AlignConsecutiveBitFields

- 连续位字段的语句的对齐

  - **Enabled**：是否启用对齐

    - `true`：

      ```c++
      int aaaa : 1;
      int b    : 12;
      int ccc  : 8;
      ```

    - `false`：

      ```c++
      int aaaa : 1;
      int b : 12;
      int ccc : 8;
      ```

  - **AcrossEmptyLines**：是否跨空行对齐

    - `true`：

      ```c++
      int aaaa : 1;
      int b    : 12;
      
      int ccc  : 8;
      ```

    - `false`：

      ```c++
      int aaaa : 1;
      int b    : 12;
      
      int ccc : 8;
      ```

  - **AcrossComments**：是否跨注释对齐

    - `true`：

      ```c++
      int d   : 2;
      /* A comment. */
      int eee : 3;
      ```

    - `false`：

      ```c++
      int d : 2;
      /* A comment. */
      int eee : 3;
      ```

##### AlignConsecutiveDeclarations

- 连续声明的对齐

  - **Enabled**：是否启用对齐

    - `true`：

      ```c++
      int         aaaa = 12;
      float       b = 23;
      std::string ccc;
      ```

    - `false`：

      ```c++
      int aaaa = 12;
      float b = 23;
      std::string ccc;
      ```

  - **AcrossEmptyLines**：是否跨空行对齐

    - `true`：

      ```c++
      int         aaaa = 12;
      float       b = 23;
      
      std::string ccc;
      ```

    - `false`：

      ```c++
      int   aaaa = 12;
      float b = 23;
      
      std::string ccc;
      ```

  - **AcrossComments**：是否跨注释对齐

    - `true`：

      ```c++
      int         aaaa = 12;
      float       b = 23;
      /* A comment. */
      std::string ccc;
      ```

    - `false`：

      ```c++
      int   aaaa = 12;
      float b = 23;
      /* A comment. */
      std::string ccc;
      ```

##### AlignConsecutiveMacros

- 连续宏定义的对齐

  - **Enabled**：是否启用对齐

    - `true`：

      ```c++
      #define SHORT_NAME  42
      #define LONGER_NAME 0x007f
      #define foo(x)      (x * x)
      #define bar(y, z)   (y + z)
      ```

    - `false`：

      ```c++
      #define SHORT_NAME 42
      #define LONGER_NAME 0x007f
      #define foo(x) (x * x)
      #define bar(y, z) (y + z)
      ```

  - **AcrossEmptyLines**：是否跨空行对齐

    - `true`：

      ```c++
      #define SHORT_NAME  42
      #define LONGER_NAME 0x007f
      
      #define foo(x)      (x * x)
      ```

    - `false`：

      ```c++
      #define SHORT_NAME  42
      #define LONGER_NAME 0x007f
      
      #define foo(x) (x * x)
      ```

  - **AcrossComments**：是否跨注释对齐

    - `true`：

      ```c++
      #define SHORT_NAME  42
      #define LONGER_NAME 0x007f
      /* A comment. */
      #define foo(x)      (x * x)
      ```

    - `false`：

      ```c++
      #define SHORT_NAME  42
      #define LONGER_NAME 0x007f
      /* A comment. */
      #define foo(x) (x * x)
      ```

##### AlignConsecutiveShortCaseStatements

- 连续小写标签的对齐，仅当`AllowShortCaseLabelsOnASingleLine`为`true`时适用。

  - **Enabled**：是否启用对齐

    - `true`：

      ```c++
      switch (level) {
      case log::info:    return "info:";
      case log::warning: return "warning:";
      default:           return "";
      }
      ```

    - `false`：

      ```c++
      switch (level) {
      case log::info: return "info:";
      case log::warning: return "warning:";
      default: return "";
      }
      ```

  - **AcrossEmptyLines**：是否跨空行对齐

    - `true`：

      ```c++
      switch (level) {
      case log::info:    return "info:";
      case log::warning: return "warning:";
      
      default:           return "";
      ```

    - `false`：

      ```c++
      switch (level) {
      case log::info:    return "info:";
      case log::warning: return "warning:";
      
      default: return "";
      }
      ```

  - **AcrossComments**：是否跨注释对齐

    - `true`：

      ```c++
      switch (level) {
      case log::info:    return "info:";
      case log::warning: return "warning:";
      /* A comment. */
      default:           return "";
      }
      ```

    - `false`：

      ```c++
      switch (level) {
      case log::info:    return "info:";
      case log::warning: return "warning:";
      /* A comment. */
      default: return "";
      }
      ```

  - **AlignCaseColons**：case标签是在冒号上对齐，还是在冒号后的标记上对齐

    - `true`：

      ```c++
      switch (level) {
      case log::info   : return "info:";
      case log::warning: return "warning:";
      default          : return "";
      }
      ```

    - `false`：

      ```c++
      switch (level) {
      case log::info:    return "info:";
      case log::warning: return "warning:";
      default:           return "";
      }
      ```

##### AlignEscapedNewlines

- 续行符(\\)对齐

  - `DontAlign`：不对齐

    ```c++
    #define A \
        int aaaa; \
        int b; \
        int dddddddddd;
    ```

  - `Left`：尽可能左对齐

    ```c++
    #define A     \
        int aaaa; \
        int b;    \
        int dddddddddd;
    ```

  - `Right`：尽可能右对齐

    ```c++
    #define A                                                    \
        int aaaa;                                                \
        int b;                                                   \
        int dddddddddd;
    ```

##### AlignOperands

- 二元和三元表达式的操作数水平对齐

  - `DontAlign`：不对齐二元和三元表达式的操作数，换行后的行从行首开始缩进`ContinuationIndentWidth`空格

    ```c++
    int a = 11111111 + 22222222 + 33333333 + 44444444 + 55555555 + 66666666 +
        77777777;
    ```

  - `Align`：

    - 水平对齐二进制和三元表达式的操作数

      ```c++
      int a = 11111111 + 22222222 + 33333333 + 44444444 + 55555555 + 66666666 +
              77777777;
      ```

    - 当`BreakBeforeBinaryOperators`被设置时，被包装的操作符与操作数在第一行对齐

      ```c++
      int a = 11111111 + 22222222 + 33333333 + 44444444 + 55555555 + 66666666
              + 77777777;
      ```

  - `AlignAfterOperator`：水平对齐二进制和三元表达式的操作数，这类似于 `Align` ，除了当 `BreakBeforeBinaryOperators` 被设置时，该操作符是不缩进的，以便被包装的操作数在第一行与操作数对齐

    ```c++
    int a = 11111111 + 22222222 + 33333333 + 44444444 + 55555555 + 66666666
          + 77777777;
    ```

##### AlignTrailingComments

- 尾随注释的对齐

  - **Kind** ：指定尾随注释对齐的方式

    - `Leave`：保持尾随注释不变

      ```c++
      int a; // comment
      int abcde;       // comment
      ```

    - `Always`：对齐尾随注释

      ```c++
      int a;     // comment
      int abcde; // comment
      ```

    - `Never`：不对齐尾随注释，但其他格式化程序适用

      ```c++
      int a; // comment
      int abcde; // comment
      ```

  - **OverEmptyLines**：对齐时可间隔的空行数

    - 当`MaxEmptyLinesToKeep`和`OverEmptyLines`都设置为2时：

      ```c++
      int a;      // all these
      
      int ab;     // comments are
      
      
      int abcdef; // aligned
      ```

    - 当`MaxEmptyLinesToKeep`设置为2，`OverEmptyLines`设置为1时：

      ```c++
      int a;  // these are
      
      int ab; // aligned
      
      
      int abcdef; // but this isn't
      ```

##### AllowAllArgumentsOnNextLine

- 如果函数调用或花括号的初始化列表不能放在一行中，则允许将所有参数放到下一行，即使 `BinPackArguments`为 `false`

  - `true`：

    ```c++
    callFunction(
        a, b, c, d);
    ```

  - `false`：

    ```c++
    callFunction(a,
                 b,
                 c,
                 d);
    ```

##### AllowAllConstructorInitializersOnNextLine

- 此选项已弃用，请参考`PackConstructorInitializers`的 `NextLine`。

##### AllowAllParametersOfDeclarationOnNextLine

- 如果函数声明不适合一行，则允许将函数声明的所有参数放到下一行，即使 `BinPackArguments`为 `false`

  - `true`：

    ```c++
    void myFunction(
        int a, int b, int c, int d, int e);
    ```

  - `false`：

    ```c++
    void myFunction(int a,
                    int b,
                    int c,
                    int d,
                    int e);
    ```

##### AllowShortBlocksOnASingleLine

- 依赖于值，`while (true) { continue; }` 可以放在一行上

  - `Never`：永远不要将块合并为一行

    ```c++
    while (true) {
    }
    while (true) {
        continue;
    }
    ```

  - `Empty`：只合并空块

    ```c++
    while (true) {}
    while (true) {
        continue;
    }
    ```

  - `Always`：总是将短块合并为一行

    ```c++
    while (true) {}
    while (true) { continue; }
    ```

##### AllowShortCaseLabelsOnASingleLine

- 如果为 `true`，短 `case` 标签将收缩为一行。

  - `true`：

    ```c++
    switch (a) {
    case 1: x = 1; break;
    case 2: return;
    }
    ```

  - `false`：

    ```c++
    switch (a) {
    case 1:
      x = 1;
      break;
    case 2:
      return;
    }
    ```

##### AllowShortEnumsOnASingleLine

- 允许在单行上使用短的枚举

  - `true`：

    ```c++
    enum { A, B } myEnum;
    ```

  - `false`：

    ```c++
    enum
    {
        A,
        B
    } myEnum;
    ```

##### AllowShortFunctionsOnASingleLine

- 根据值，短函数`int f() { return 0; }` 可以放在一行上

  - `None`：永远不要将函数合并到一行中

  - `InlineOnly`：只合并类中定义的函数。与 `Inline` 相同，除了它不暗含 `Empty`: 即顶层空函数也不合并

    ```c++
    class Foo {
        void f() { foo(); }
    };
    void f() {
        foo();
    }
    void f() {
    }
    ```

  - `Empty`：只合并空函数

    ```c++
    void f() {}
    void f2() {
        bar2();
    }
    ```

  - `Inline`：只合并类中定义的函数。暗含 `Empty`

    ```c++
    class Foo {
        void f() { foo(); }
    };
    void f() {
        foo();
    }
    void f() {}
    ```

  - `All`： 将所有函数合并到一行中

    ```c++
    class Foo {
        void f() { foo(); }
    };
    void f() { bar(); }
    ```

##### AllowShortIfStatementsOnASingleLine

- 如果为 `true`，则 `if (a) return;` 可以放在一行

  - `Never`：永远不要把简短的 `if` 放在同一行上

    ```c++
    if (a)
        return;
    
    if (b)
        return;
    else
        return;
    
    if (c)
        return;
    else {
        return;
    }
    ```

  - `WithoutElse`：没有 `else`语句时，才将短 `if` 放在同一行

    ```c++
    if (a) return;
    
    if (b)
        return;
    else
        return;
    
    if (c)
        return;
    else {
        return;
    }
    ```

  - `OnlyFirstIf`：只有第一个`if`允许

    ```c++
    if (a) return;
    
    if (b) return;
    else if (b)
        return;
    else
        return;
    
    if (c) return;
    else {
        return;
    }
    ```

  - `AllIfsAndElse`：始终将简短的`if`、`else if`和`else`语句放在同一行

    ```c++
    if (a) return;
    
    if (b) return;
    else return;
    
    if (c) return;
    else {
        return;
    }
    ```

##### AllowShortLambdasOnASingleLine

- 依赖于值，`auto lambda []() { return 0; }` 可以放在一行上

  - `None`：永远不要将 `lambda` 合并到一行中

  - `Empty`：只合并空的 `lambda`

    ```c++
    auto lambda = [](int a) {}
    auto lambda2 = [](int a) {
        return a;
    };
    ```

  - `Inline`： 如果`lambda` 是函数的参数则合并为一行

    ```c++
    auto lambda = [](int a) {
        return a;
    };
    sort(a.begin(), a.end(), ()[] { return x < y; })
    ```

  - `All`：将所有符合的 `lambda` 合并到一行上

    ```c++
    auto lambda = [](int a) {}
    auto lambda2 = [](int a) { return a; };
    ```

##### AllowShortLoopsOnASingleLine

- 如果为 `true` ，则 `while (true) continue;` 可以放在一行上

  - `true`：

    ```c++
    while (true) { int i = 1; }
    ```

  - `false`：

    ```c++
    while (true) {
        int i = 1;
    }
    ```

##### AlwaysBreakAfterDefinitionReturnType

- 该选项已弃用，为了向后兼容而保留。

##### AlwaysBreakAfterReturnType

- 函数声明返回类型的换行样式

  - `None`：返回类型后自动换行

    ```c++
    class A {
        int f() { return 0; };
    };
    int f();
    int f() { return 1; }
    
    ```

  - `All`：总是在返回类型之后换行

    ```c++
    class A {
    int
    f() {
        return 0;
    };
    };
    int
    f();
    int
    f() {
        return 1;
    }
    ```

  - `TopLevel`：总是在顶级函数的返回类型之后换行

    ```c++
    class A {
        int f() { return 0; };
    };
    int
    f();
    int
    f() {
        return 1;
    }
    ```

  - `AllDefinitions`：总是在函数定义的返回类型之后换行

    ```c++
    class A {
    int
    f() {
        return 0;
    };
    };
    int f();
    int
    f() {
        return 1;
    }
    ```

  - `TopLevelDefinitions`：总是在顶级定义的返回类型之后换行

    ```c++
    class A {
        int f() { return 0; };
    };
    int f();
    int
    f() {
        return 1;
    }
    ```

##### AlwaysBreakBeforeMultilineStrings

- 如果为 `true`，总是在多行字符串字面值之前换行

- 这个标志是为了使文件中有多个多行字符串的情况看起来更一致。因此，只有在此时包装字符串导致从行开始的`ContinuationIndentWidth`空格缩进时，它才会生效

  - `true`：

    ```c++
    aaaa =
        "bbbb"
        "cccc";
    ```

  - false：

    ```c++
    aaaa = "bbbb"
           "cccc";
    ```

##### AlwaysBreakTemplateDeclarations

- 模板声明换行样式

  - `No`：在声明之前不强制换行，`PenaltyBreakTemplateDeclaration`也被考虑在内

    ```c++
    template <typename T> T foo() {
    }
    template <typename T> T foo(int aaaaaaaaaaaaaaaaaaaaa,
                                int bbbbbbbbbbbbbbbbbbbbb) {
    }
    ```

  - `MultiLine`：只有当下列声明跨多行时，才在模板声明后强制换行

    ```c++
    template <typename T> T foo() {
    }
    template <typename T>
    T foo(int aaaaaaaaaaaaaaaaaaaaa,
        int bbbbbbbbbbbbbbbbbbbbb) {
    }
    ```

  - `Yes`：总是在模板声明之后换行

    ```c++
    template <typename T>
    T foo() {
    }
    template <typename T>
    T foo(int aaaaaaaaaaaaaaaaaaaaa,
        int bbbbbbbbbbbbbbbbbbbbb) {
    }
    ```

##### AttributeMacros

- 一个字符串列表被解释为属性/限定符，而不是标识符, 用于语言扩展或静态分析注解，例如：

  ```c++
  x = (char *__capability)&y;
  int function(void) __ununsed;
  void only_writes_to_buffer(char *__output buffer);
  ```

  在 `.clang-format` 配置文件中，可以这样配置：

  ```c++
  AttributeMacros: ['__capability', '__output', '__ununsed']
  ```

##### BinPackArguments

- 如果为 `false`，函数调用的参数要么都在同一行，要么各一行

  - `true`：

    ```c++
    void f() {
      f(aaaaaaaaaaaaaaaaaaaa, aaaaaaaaaaaaaaaaaaaa,
        aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa);
    }
    ```

  - `false`：

    ```c++
    void f() {
      f(aaaaaaaaaaaaaaaaaaaa,
        aaaaaaaaaaaaaaaaaaaa,
        aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa);
    }
    ```

##### BinPackParameters

- 如果为 `false`，函数声明或函数定义的形参要么都在同一行，要么各有一行

- - `true`：

    ```c++
    void f(int aaaaaaaaaaaaaaaaaaaa, int aaaaaaaaaaaaaaaaaaaa,
           int aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa) {}
    ```

  - `false`：

    ```c++
    void f(int aaaaaaaaaaaaaaaaaaaa,
           int aaaaaaaaaaaaaaaaaaaa,
           int aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa) {}
    ```

##### BitFieldColonSpacing

- 用于位字段的空格样式

  - `Both`：每边加一个空格

    ```c++
    unsigned bf : 2;
    ```

  - `None`：周围不添加空格（除非需要`AlignConsecutiveBitFields`）

    ```c++
    unsigned bf:2;
    ```

  - `Before`：在`:`之前增加一个空格

  - ```c++
    unsigned bf :2;
    ```

  - `After`：在`:`之后增加一个空格（如果`AlignConsecutiveBitFields`需要的话，可以在前面加空格）

    ```c++
    unsigned bf: 2;
    ```

##### BraceWrapping

- 控制大括号换行情况，如果`BreakBeforeBraces`被设置为 `Custom`，使用这个来指定应该如何处理每个单独的大括号。否则，这将被忽略

  - **AfterCaseLabel**：`case` 标签的括号

    - `true`：

      ```c++
      switch (foo) {
          case 1:
          {
              bar();
              break;
          }
          default:
          {
              plop();
          }
      }
      ```

    - `false`：

      ```c++
      switch (foo) {
          case 1: {
              bar();
              break;
          }
          default: {
              plop();
          }
      }
      ```

  - **AfterClass**：`class` 定义的括号

    - `true`：

      ```c++
      class foo {};
      ```

    - `false`：

      ```c++
      class foo
      {};
      ```

  - **AfterControlStatement**：包含控制语句 (`if`/`for`/`while`/`switch`/…)

    - `Never`：永远不换行, 即永远将语句体的大括号放置于控制语句同一行

      ```c++
      if (foo()) {
      } else {
      }
      for (int i = 0; i < 10; ++i) {
      }
      ```

    - `MultiLine`：多行控制语句才进行换行

      ```c++
      if (foo && bar &&
          baz)
      {
          quux();
      }
      while (foo || bar) {
      }
      ```

    - `Always`：总是换行

      ```c++
      if (foo())
      {
      } else
      {}
      for (int i = 0; i < 10; ++i)
      {}
      ```

  - **AfterEnum**：`enum`定义的括号

    - `true`：

      ```c++
      enum X : int
      {
          B
      };
      ```

    - `false`：

      ```c++
      enum X : int { B };
      ```

  - **AfterFunction**：函数定义的括号

    - `true`：

      ```c++
      void foo()
      {
          bar();
          bar2();
      }
      ```

    - `false`：

      ```c++
      void foo() {
          bar();
          bar2();
      }
      ```

  - **AfterNamespace**：`namespace` 定义的括号

    - `true`：****

      ```c++
      namespace
      {
          int foo();
          int bar();
      }
      ```

    - `false`：

      ```c++
      namespace {
          int foo();
          int bar();
      }
      ```

  - **AfterStruct**：`struct` 定义的括号

    - `true`：

      ```c++
      struct foo
      {
          int x;
      };
      ```

    - `false`：

      ```c++
      struct foo {
          int x;
      };
      ```

  - **AfterUnion**：`union` 定义的括号

    - `true`：

      ```c++
      union foo
      {
          int x;
      }
      ```

    - `false`：

      ```c++
      union foo {
          int x;
      }
      ```

  - **AfterExternBlock**：`extern` 定义的括号

    - `true`：

      ```c++
      extern "C"
      {
      int foo();
      }
      ```

    - `false`：

      ```c++
      extern "C" {
      int foo();
      }
      ```

  - **BeforeCatch**：`catch` 之前的括号

    - `true`：

      ```c++
      try {
          foo();
      }
      catch () {
      }
      ```

    - `false`：

      ```c++
      try {
          foo();
      } catch () {
      }
      ```

  - **BeforeElse**：`else` 之前的括号

    - `true`：

      ```c++
      if (foo()) {
      }
      else {
      }
      ```

    - `false`：

      ```c++
      if (foo()) {
      } else {
      }
      ```

  - **BeforeLambdaBody**：`lambda` 块的括号

    - `true`：

      ```c++
      connect(
          []()
          {
              foo();
              bar();
          });
      ```

    - `false`：

      ```c++
      connect([]() {
          foo();
          bar();
      });
      ```

  - **BeforeWhile**：`while` 前的括号

    - `true`：

      ```c++
      do {
          foo();
      }
      while (1);
      ```

    - `false`：

      ```c++
      do {
          foo();
      } while (1);
      ```

  - **IndentBraces**：缩进包装的括号本身

  - **SplitEmptyFunction**：如果为 `false`，则空函数体可以放在一行上。该选项仅在函数的左括号已经被包装的情况下使用，即设置了`AfterFunction`括号封装模式，并且该函数不可以/不应该放在单行上(如`AllowShortFunctionsOnASingleLine`和构造函数格式化选项)

    - `true`：

      ```c++
      int f()
      {
      }
      ```

    - `false`：

      ```c++
      int f()
      {}
      ```

  - **SplitEmptyRecord**：如果为 `false`，空记录(例如类，结构体或联合)主体可以放在一行上。此选项仅在记录的开括号已经被包装时使用，即设置了 `AfterClass`(对于类)括号封装模式

    - `true`：

      ```c++
      class Foo
      {
      }
      ```

    - `false`：

      ```c++
      class Foo
      {}
      ```

  - **SplitEmptyNamespace**：如果为 `false`，则空的命名空间主体可以放在一行上。该选项仅在名称空间的左大括号已经被包装时使用，即设置了 `AfterNamespace` 大括号包装模式

    - `true`：

      ```c++
      namespace Foo
      {
      }
      ```

    - `false`：

      ```c++
      namespace Foo
      {}
      ```

##### BracedInitializerIndentWidth

- 带括号的初始化列表的缩进列数。如果未设置，则使用`ContinuationIndentWidth`

  ```c++
  BracedInitializerIndentWidth: 2
  
  void f() {
    SomeClass c{
      "foo",
      "bar",
      "baz",
    };
    auto s = SomeStruct{
      .foo = "foo",
      .bar = "bar",
      .baz = "baz",
    };
    SomeArrayT a[3] = {
      {
        foo,
        bar,
      },
      {
        foo,
        bar,
      },
      SomeArrayT{},
    };
  }
  ```

##### BreakAfterAttributes

- 函数声明/定义名称前的C++11属性的换行

  - `Always`：始终在属性后换行

    ```c++
    [[nodiscard]]
    inline int f();
    [[gnu::const]] [[nodiscard]]
    int g();
    ```

  - `Leave`：保持原样

    ```c++
    [[nodiscard]] inline int f();
    [[gnu::const]] [[nodiscard]]
    int g();
    ```

  - `Never`：从不换行

    ```c++
    [[nodiscard]] inline int f();
    [[gnu::const]] [[nodiscard]] int g();
    ```

##### BreakBeforeBinaryOperators

- 二元运算符换行的方式

  - `None`：运算符之后换行

    ```c++
    LooooooooooongType loooooooooooooooooooooongVariable =
        someLooooooooooooooooongFunction();
    
    bool value = aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa +
                        aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa ==
                    aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa &&
                aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa >
                    ccccccccccccccccccccccccccccccccccccccccc;
    ```

  - `NonAssignment`：在非赋值操作符之前换行

    ```c++
    LooooooooooongType loooooooooooooooooooooongVariable =
        someLooooooooooooooooongFunction();
    
    bool value = aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
                        + aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
                    == aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
                && aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
                        > ccccccccccccccccccccccccccccccccccccccccc;
    ```

  - `All`：运算符之前换行

    ```c++
    LooooooooooongType loooooooooooooooooooooongVariable
        = someLooooooooooooooooongFunction();
    
    bool value = aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
                        + aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
                    == aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
                && aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
                        > ccccccccccccccccccccccccccccccccccccccccc;
    ```

##### BreakBeforeBraces

- 大括号换行风格

  - `Attach`：始终附加到周围的上下文中

    ```c++
    namespace N {
    enum E {
      E1,
      E2,
    };
    
    class C {
    public:
      C();
    };
    
    bool baz(int i) {
      try {
        do {
          switch (i) {
          case 1: {
            foobar();
            break;
          }
          default: {
            break;
          }
          }
        } while (--i);
        return true;
      } catch (...) {
        handleError();
        return false;
      }
    }
    
    void foo(bool b) {
      if (b) {
        baz(2);
      } else {
        baz(5);
      }
    }
    
    void bar() { foo(true); }
    } // namespace N
    ```

  - `Linux`：类似于`Attach`，但在函数、名称空间和类定义上，在大括号前断开

    ```c++
    namespace N
    {
    enum E {
      E1,
      E2,
    };
    
    class C
    {
    public:
      C();
    };
    
    bool baz(int i)
    {
      try {
        do {
          switch (i) {
          case 1: {
            foobar();
            break;
          }
          default: {
            break;
          }
          }
        } while (--i);
        return true;
      } catch (...) {
        handleError();
        return false;
      }
    }
    
    void foo(bool b)
    {
      if (b) {
        baz(2);
      } else {
        baz(5);
      }
    }
    
    void bar() { foo(true); }
    } // namespace N
    ```

  - `Mozilla`：类似于`Attach`，但在枚举、函数和记录定义上在大括号前打断

    ```c++
    namespace N {
    enum E
    {
      E1,
      E2,
    };
    
    class C
    {
    public:
      C();
    };
    
    bool baz(int i)
    {
      try {
        do {
          switch (i) {
          case 1: {
            foobar();
            break;
          }
          default: {
            break;
          }
          }
        } while (--i);
        return true;
      } catch (...) {
        handleError();
        return false;
      }
    }
    
    void foo(bool b)
    {
      if (b) {
        baz(2);
      } else {
        baz(5);
      }
    }
    
    void bar() { foo(true); }
    } // namespace N
    ```

  - `Stroustrup`：类似于Attach，但在函数定义、catch和else之前中断

    ```c++
    namespace N {
    enum E {
      E1,
      E2,
    };
    
    class C {
    public:
      C();
    };
    
    bool baz(int i)
    {
      try {
        do {
          switch (i) {
          case 1: {
            foobar();
            break;
          }
          default: {
            break;
          }
          }
        } while (--i);
        return true;
      }
      catch (...) {
        handleError();
        return false;
      }
    }
    
    void foo(bool b)
    {
      if (b) {
        baz(2);
      }
      else {
        baz(5);
      }
    }
    
    void bar() { foo(true); }
    } // namespace N
    ```

  - `Allman`：总是在括号前换行

    ```c++
    namespace N
    {
    enum E
    {
      E1,
      E2,
    };
    
    class C
    {
    public:
      C();
    };
    
    bool baz(int i)
    {
      try
      {
        do
        {
          switch (i)
          {
          case 1:
          {
            foobar();
            break;
          }
          default:
          {
            break;
          }
          }
        } while (--i);
        return true;
      }
      catch (...)
      {
        handleError();
        return false;
      }
    }
    
    void foo(bool b)
    {
      if (b)
      {
        baz(2);
      }
      else
      {
        baz(5);
      }
    }
    
    void bar() { foo(true); }
    } // namespace N
    ```

  - `Whitesmiths`：像`Allman`一样，但总是缩进大括号并用大括号排列代码

    ```c++
    namespace N
      {
    enum E
      {
      E1,
      E2,
      };
    
    class C
      {
    public:
      C();
      };
    
    bool baz(int i)
      {
      try
        {
        do
          {
          switch (i)
            {
            case 1:
            {
            foobar();
            break;
            }
            default:
            {
            break;
            }
            }
          } while (--i);
        return true;
        }
      catch (...)
        {
        handleError();
        return false;
        }
      }
    
    void foo(bool b)
      {
      if (b)
        {
        baz(2);
        }
      else
        {
        baz(5);
        }
      }
    
    void bar() { foo(true); }
      } // namespace N
    ```

  - `GNU`：始终在大括号前打断，并在控制语句的大括号上添加额外的缩进级别，而不是在类、函数或其他定义的大括号中

    ```c++
    namespace N
    {
    enum E
    {
      E1,
      E2,
    };
    
    class C
    {
    public:
      C();
    };
    
    bool baz(int i)
    {
      try
        {
          do
            {
              switch (i)
                {
                case 1:
                  {
                    foobar();
                    break;
                  }
                default:
                  {
                    break;
                  }
                }
            }
          while (--i);
          return true;
        }
      catch (...)
        {
          handleError();
          return false;
        }
    }
    
    void foo(bool b)
    {
      if (b)
        {
          baz(2);
        }
      else
        {
          baz(5);
        }
    }
    
    void bar() { foo(true); }
    } // namespace N
    ```

  - `WebKit`：类似于Attach，但在函数之前先断开

    ```c++
    namespace N {
    enum E {
      E1,
      E2,
    };
    
    class C {
    public:
      C();
    };
    
    bool baz(int i)
    {
      try {
        do {
          switch (i) {
          case 1: {
            foobar();
            break;
          }
          default: {
            break;
          }
          }
        } while (--i);
        return true;
      } catch (...) {
        handleError();
        return false;
      }
    }
    
    void foo(bool b)
    {
      if (b) {
        baz(2);
      } else {
        baz(5);
      }
    }
    
    void bar() { foo(true); }
    } // namespace N
    ```

  - `Custom`：在BraceWrapping中配置每个单独的括号

##### BreakBeforeConceptDeclarations

- 要使用的`concept`声明样式

  - `Never`：将模板声明行与`concept`放在一起

    ```c++
    template <typename T> concept C = ...;
    ```

  - `Allowed`：允许在模板声明和`concept`之间进行拆分。实际行为取决于内容、违规规则和处罚

  - `Always`：始终在`concept`之前换行，将其放在模板声明之后的行中

    ```c++
    template <typename T>
    concept C = ...;
    ```

##### BreakBeforeInlineASMColon

- 要使用的内联ASM冒号样式

  - `Never`：内联ASM冒号前不换行

    ```c++
    asm volatile("string", : : val);
    ```

  - `OnlyMultiline`：如果行长度超过列限制，在内联ASM冒号之前换行

    ```c++
    asm volatile("string", : : val);
    asm("cmoveq %1, %2, %[result]"
        : [result] "=r"(result)
        : "r"(test), "r"(new), "[result]"(old));
    ```

  - `Always`：总是在内联ASM冒号之前换行

    ```c++
    asm volatile("string",
                 :
                 : val);
    ```

##### BreakBeforeTernaryOperators

- 如果为 `true`，将在换行符之后放置三元操作符

  - `true`：

    ```c++
    veryVeryVeryVeryVeryVeryVeryVeryVeryVeryVeryLongDescription
        ? firstValue
        : SecondValueVeryVeryVeryVeryLong;
    ```

  - `false`：

    ```c++
    veryVeryVeryVeryVeryVeryVeryVeryVeryVeryVeryLongDescription ?
        firstValue :
        SecondValueVeryVeryVeryVeryLong;
    ```

##### BreakConstructorInitializers

- 要使用的构造函数初始化式样式

  - `BeforeColon`：在冒号之前和逗号之后换行

    ```c++
    Constructor()
        : initializer1(),
        initializer2()
    ```

  - `BeforeComma`：在冒号和逗号之前换行，并将逗号与冒号对齐

    ```c++
    Constructor()
        : initializer1()
        , initializer2()
    ```

  - `AfterColon`：在冒号和逗号后换行

    ```c++
    Constructor() :
        initializer1(),
        initializer2()
    ```

##### BreakInheritanceList

- 要使用的继承列表样式

  - `BeforeColon`：在冒号之前和逗号之后换行

    ```c++
    class Foo
        : Base1,
        Base2
    {};
    ```

  - `BeforeComma`：在冒号和逗号之前换行，并将逗号与冒号对齐

    ```c++
    class Foo
        : Base1
        , Base2
    {};
    ```

  - `AfterColon`：在冒号和逗号后换行

    ```c++
    class Foo :
        Base1,
        Base2
    {};
    ```

##### BreakStringLiterals

- 允许在格式化字面值常量时换行

  - `true`：

    ```c++
    const char* x = "veryVeryVeryVeryVeryVe"
                    "ryVeryVeryVeryVeryVery"
                    "VeryLongString";
    ```

  - `false`：

    ```c++
    const char* x =
        "veryVeryVeryVeryVeryVeryVeryVeryVeryVeryVeryVeryLongString";
    ```

##### ColumnLimit

- 列限制
- 列限制为 `0` 意味着没有列限制。在这种情况下，`clang-format` 将在语句中尊重输入的断行决定，除非它们与其他规则相抵触

##### CommentPragmas

- 描述具有特殊含义的注释的正则表达式，不应将其拆分为行或以其他方式更改

##### CompactNamespaces

- 如果为 `true`，连续的名称空间声明将在同一行上。如果为 `false`，则每个名称空间都声明在一个新的行中

  - `true`：

    ```c++
    namespace Foo { namespace Bar {
    }}
    ```

  - `false`：

    ```c++
    namespace Foo {
    namespace Bar {
    }
    }
    ```

##### ConstructorInitializerIndentWidth

- 用于缩进构造函数初始化列表和继承列表的字符数

##### ContinuationIndentWidth

- 连续行缩进宽度

  ```c++
  ContinuationIndentWidth: 2
  
  int i =         //  VeryVeryVeryVeryVeryLongComment
    longFunction( // Again a long comment
      arg);
  ```

##### Cpp11BracedListStyle

- 如果为 `true`，将带大括号的列表格式化为最适合 `C++11` 带大括号的列表

  - 括号内没有空格。

  - 在右括号之前不能换行。

  - 使用延续缩进，而不是使用块缩进。

  - `true`：

    ```c++
    vector<int> x{1, 2, 3, 4};
    vector<T> x{{}, {}, {}, {}};
    f(MyMap[{composite, key}]);
    new int[3]{1, 2, 3};
    ```

  - `false`：

    ```c++
    vector<int> x{ 1, 2, 3, 4 };
    vector<T> x{ {}, {}, {}, {} };
    f(MyMap[{ composite, key }]);
    new int[3]{ 1, 2, 3 };
    ```

##### DeriveLineEnding

- 如果为 `true`，分析格式化文件中最常用的行结束符(`\r\n`或`\n`)。只有当没有派生项时，`UseCRLF`才用作后备

##### DerivePointerAlignment

- 如果为 `true`，分析格式化文件，以确定最常见的 `&` 和 `*` 对齐方式。指针和引用对齐样式将根据文件中找到的首选项进行更新。然后，`PointerAlignment`仅用作后备

##### DisableForma

- 完全禁用格式化

##### EmptyLineAfterAccessModifier

- 定义何时在访问修饰符后放置空行。 `EmptyLineBeforeAccessModifier` 配置处理两个访问修饰符之间的空行数

  - `Never`：删除访问修饰符后的所有空行

    ```c++
    struct foo {
    private:
      int i;
    protected:
      int j;
      /* comment */
    public:
      foo() {}
    private:
    protected:
    };
    ```

  - `Leave`：在访问修饰符之后保留现有的空行，使用`MaxEmptyLinesToKeep`

  - `Always`：如果没有访问修饰符，请始终在访问修饰符后添加空行，使用`MaxEmptyLinesToKeep`

    ```c++
    struct foo {
    private:
    
      int i;
    protected:
    
      int j;
      /* comment */
    public:
    
      foo() {}
    private:
    
    protected:
    
    };
    ```

##### EmptyLineBeforeAccessModifier

- 定义在何种情况下在访问修饰符之前放置空行

  - `Never`：删除访问修饰符之前的所有空行

    ```c++
    struct foo {
    private:
      int i;
    protected:
      int j;
      /* comment */
    public:
      foo() {}
    private:
    protected:
    };
    ```

  - `Leave`：在访问修饰符之前保持现有的空行

  - `LogicalBlock`：只有当访问修饰符开始一个新的逻辑块时才添加空行。逻辑块是由一个或多个成员字段或函数组成的一组

    ```c++
    struct foo {
    private:
      int i;
    
    protected:
      int j;
      /* comment */
    public:
      foo() {}
    
    private:
    protected:
    };
    ```

  - `Always`：总是在访问修饰符之前添加空行，除非访问修饰符位于结构或类定义的开头

    ```c++
    struct foo {
    private:
      int i;
    
    protected:
      int j;
      /* comment */
    
    public:
      foo() {}
    
    private:
    
    protected:
    };
    ```

##### ExperimentalAutoDetectBinPacking

- 如果为 `true`, `clang-format` 将检测函数调用和定义是否每行使用一个参数进行格式化。

  每个调用都可以被包含，每行或不确定。如果它是不确定的，例如完全在一行上，但需要做出决定，`clang-format` 分析输入文件中是否有其他包含情况，并相应地采取行动。

- 这是一个实验性的标志，它可能会消失或被重命名。不要在配置文件中使用它，等等。使用时自负风险

##### FixNamespaceComments

- 如果为 `true`, `clang-format` 将为短名称空间添加缺失的名称空间结束注释，并修复无效的现有名称空间。短的由`ShortNamespaceLines`控制

  - `true`：

    ```c++
    namespace a {
        foo();
        bar();
    } // namespace a
    ```

  - `false`：

    ```c++
    namespace a {
        foo();
        bar();
    }
    ```

##### ForEachMacros

- 宏的矢量，应该解释为 `foreach` 循环，而不是函数调用，例如：

  ```c++
  FOREACH(<variable-declaration>, ...)
    <loop-body>
  ```

- 在 `.clang-format` 配置文件中，可以这样配置：

  ```c++
  ForEachMacros: ['RANGES_FOR', 'FOREACH']
  ```

##### IfMacros

- 应解释为条件而不是函数调用的宏向量，例如：

  ```c++
  IF(...)
    <conditional-body>
  else IF(...)
    <conditional-body>
  ```

- 在 `.clang-format` 配置文件中，可以这样配置：

  ```c++
  IfMacros: ['IF']
  ```

##### IncludeBlocks

- 根据这个值，可以将多个 `#include` 块按类别排序

  - `Preserve`：分别对每个 `#include` 块进行排序

    ```c++
    #include "b.h"               into      #include "b.h"
    
    #include <lib/main.h>                  #include "a.h"
    #include "a.h"                         #include <lib/main.h>
    ```

  - `Merge`：将多个 `#include` 块合并在一起，并按一个排序

    ```c++
    #include "b.h"               into      #include "a.h"
                                           #include "b.h"
    #include <lib/main.h>                  #include <lib/main.h>
    #include "a.h"
    ```

  - `Regroup`：将多个 `#include` 块合并在一起，并按一个排序。然后根据类别优先级分组。参考`IncludeCategories`

    ```c++
    #include "b.h"               into      #include "a.h"
                                           #include "b.h"
    #include <lib/main.h>
    #include "a.h"                         #include <lib/main.h>
    ```

##### IncludeCategories

- 正则表达式表示用于排序 `#include` 的不同 `#include` 类别

- 支持 [POSIX](https://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap09.html) 扩展正则表达式。

- 这些正则表达式按顺序匹配包含的文件名(包括 `<>`或 `""`)。分配属于第一个匹配正则表达式的值，`#include` 首先根据类别编号递增排序，然后在每个类别内按字母顺序排序。

- 如果所有正则表达式都不匹配，则 `INT_MAX` 被分配为类别。源文件的主标题自动获得类别 `0`。因此它通常保存在 `#include` (https://llvm.org/docs/CodingStandards.html#include-style) 的开头。然而，如果你有某些总是需要优先的头，你也可以分配负优先级。

- 当 `IncludeBlocks = IBS_Regroup` 时，可以使用第三个可选字段 `SortPriority` 来定义 `#include` 应该被排序的优先级。`Priority` 的值定义了 `#include` 块的顺序，也允许对不同优先级的 `#include` 块进行分组。如果没有分配 `SortPriority`，则将其设置为 `Priority` 的默认值。

- 每个正则表达式都可以用大小写敏感字段标记为区分大小写，但默认情况下它不是。

- 要在 `.clang-format` 文件中配置它，请使用：

  ```c++
  IncludeCategories:
    - Regex:           '^"(llvm|llvm-c|clang|clang-c)/'
      Priority:        2
      SortPriority:    2
      CaseSensitive:   true
    - Regex:           '^(<|"(gtest|gmock|isl|json)/)'
      Priority:        3
    - Regex:           '<[[:alnum:].]+>'
      Priority:        4
    - Regex:           '.*'
      Priority:        1
      SortPriority:    0
  ```

##### IncludeIsMainRegex

- 指定在 `file-to-main-include` 映射中允许的后缀的正则表达式
- 当猜测 `#include` 是否是 `main` `include` 时(为类别 `0` 赋值，见上面)，使用这个允许后缀的正则表达式到标题干。完成部分匹配，因此:
  - "" 表示 “任意后缀”
  - "$" 表示 “没有后缀”
- 例如，如果配置为 `(_test)?$`，则头文件 `a.h` 将被视为 `a.cc` 和 `a_test.cc` 中的 `main`

##### IncludeIsMainSourceRegex

- 为在 `file-to-main-include` 映射中允许被视为 `main` 的格式化文件指定一个正则表达式。
- 默认情况下，只有当文件以: `.c`，`.cc`，`.cpp`，`.c++`，`.cxx`，`.m` 或 `.mm` 扩展名结束时，`clang-format`才会将文件视为 `main`。对于这些文件，会猜测 `main` include(要分配类别`0`，参见上面)。这个配置选项允许附加后缀和扩展名的文件被视为`main`。
- 例如，如果这个选项被配置为 `(Impl\.hpp)$`，那么一个文件 `ClassImpl.hpp` 被认为是`main`(除了 `Class.c`、`Class.cc`、`Class.cpp` 等)和 `main include file` 逻辑将被执行(稍后阶段还将使用 [IncludeIsMainRegex](https://tqfx.org/clang-format/IncludeIsMainRegex) 设置)。如果不设置此选项，`ClassImpl.hpp` 不会把主要的包含文件放在任何其他包含文件之前

##### IndentAccessModifiers

- 指定访问修饰符是否应该有自己的缩进级别。

- 当为 `false` 时，访问修饰符相对于记录成员缩进(或退缩)，表示`AccessModifierOffset`。记录成员缩进比记录低一级。当为 `true` 时，访问修饰符将获得自己的缩进级别。因此，记录成员总是比记录缩进 `2` 级，而不管是否存在访问修饰符。忽略`AccessModifierOffset`的值

  - `true`：

    ```c++
    class C {
        class D {
            void bar();
            protected:
            D();
        };
        public:
            C();
    };
    void foo() {
        return 1;
    }
    ```

  - `false`：

    ```c++
    class C {
        class D {
            void bar();
        protected:
            D();
        };
    public:
        C();
    };
    void foo() {
        return 1;
    }
    ```

##### IndentCaseBlocks

- 缩进 `case` 标签阻塞 `case` 标签的一级。

- 当为 `false` 时，`case` 标签后面的块使用与 `case` 标签相同的缩进级别，将 `case` 标签视为if语句。当为 `true` 时，该块作为范围块缩进

  - `true`：

    ```c++
    switch (fool) {
    case 1:
      {
        bar();
      }
      break;
    default:
      {
        plop();
      }
    }
    ```

  - `false`：

    ```c++
    switch (fool) {
    case 1: {
      bar();
    } break;
    default: {
      plop();
    }
    }
    ```

##### IndentCaseLabels

- 缩进 `case` 标记 `switch` 语句的一个级别。

- 当为 `false` 时，使用与 `switch` 语句相同的缩进级别。`switch` 语句体总是比 `case` 标签缩进一级( `case` 标签后面的第一个块除外，它本身会缩进代码——除非启用了`IndentCaseBlocks`)

  - `true`：

    ```c++
    switch (fool) {
      case 1:
        bar();
        break;
      default:
        plop();
    }
    ```

  - `false`：

    ```c++
    switch (fool) {
    case 1:
        bar();
        break;
    default:
        plop();
    }
    ```

##### IndentExternBlock

- `IndentExternBlockStyle` 是 `extern` 块的缩进类型

  - `AfterExternBlock`：向后兼容`AfterExternBlock`的缩进

    ```c++
    IndentExternBlock: AfterExternBlock
    BraceWrapping.AfterExternBlock: true
    extern "C"
    {
        void foo();
    }
    ```

    ```c++
    IndentExternBlock: AfterExternBlock
    BraceWrapping.AfterExternBlock: false
    extern "C" {
    void foo();
    }
    ```

  - `NoIndent`：不缩进外部块

    ```c++
    extern "C" {
    void foo();
    }
    ```

  - `Indent`：缩进外部块

    ```c++
    extern "C" {
        void foo();
    }
    ```

##### IndentGotoLabels

- 缩进 `goto` 标签。

- 当为 `false` 时，`goto` 标签被推到最左侧

  - `true`：

    ```c++
    int f() {
        if (foo()) {
        label1:
            bar();
    }
    label2:
        return 1;
    }
    ```

  - `false`：

    ```c++
    int f() {
        if (foo()) {
    label1:
            bar();
    }
    label2:
        return 1;
    }
    ```

##### IndentPPDirectives

- 要使用的预处理器指令缩进样式

  - `None`：不缩进任何指令

    ```c++
    #if FOO
    #if BAR
    #include <foo>
    #endif
    #endif
    ```

  - `AfterHash`：缩进`#`后的指令

    ```c++
    #if FOO
    #  if BAR
    #    include <foo>
    #  endif
    #endif
    ```

  - `BeforeHash`：在`#`前缩进指令

    ```c++
    #if FOO
      #if BAR
        #include <foo>
      #endif
    #endif
    ```

##### IndentRequiresClause

- 在模板中缩进 `requires` 子句

  - `true`：

    ```c++
    template <typename It>
        requires Iterator<It>
    void sort(It begin, It end) {
    //....
    }
    ```

  - `false`：

    ```c++
    template <typename It>
    requires Iterator<It>
    void sort(It begin, It end) {
    //....
    }
    ```

##### IndentWidth

- 用于缩进的列数

  ```c++
  IndentWidth: 4
  void f() {
      someFunction();
      if (true, false) {
         f();
      }
  }
  ```

##### IndentWrappedFunctionNames

- 如果函数定义或声明包装在类型之后，则缩进

  - `true`：

    ```c++
    LoooooooooooooooooooooooooooooooooooooooongReturnType
        LoooooooooooooooooooooooooooooooongFunctionDeclaration();
    ```

  - `false`：

    ```c++
    LoooooooooooooooooooooooooooooooooooooooongReturnType
    LoooooooooooooooooooooooooooooooongFunctionDeclaration();
    ```

##### InsertBraces

- 在C++中的控制语句（if、else、for、do和while）后插入大括号，除非控制语句在宏定义内，或者大括号会包含预处理器指令

  - `true`：

    ```c++
    if (isa<FunctionDecl>(D))
    {
        handleFunctionDecl(D);
    }
    else if (isa<VarDecl>(D))
    {
        handleVarDecl(D);
    }
    else
    {
        return;
    }
    
    while (i--)
    {
        for (auto *A : D.attrs()) { handleAttr(A); }
    }
    
    do {
        --i;
    } while (i);
    ```

  - `false`：

    ```c++
    if (isa<FunctionDecl>(D))
        handleFunctionDecl(D);
    else if (isa<VarDecl>(D))
        handleVarDecl(D);
    else
        return;
    
    while (i--)
        for (auto *A : D.attrs()) { handleAttr(A); }
    
    do
        --i;
    while (i);
    ```


> [!WARNING]
>
> 由于`clang-format`缺乏完整的语义信息，将此选项设置为`true`可能会导致错误的代码格式。因此，应格外注意检查此选项所做的代码更改

##### InsertNewlineAtEOF

- 在文件末尾插入新行

##### KeepEmptyLinesAtEOF

- 在文件末尾保留空行（最多为`MaxEmptyLinesToKeep`）

##### KeepEmptyLinesAtTheStartOfBlocks

- 如果为 `true`，则保留块开头的空行

  - `true`：

    ```c++
    if (foo) {
        bar();
    }
    ```

  - `false`：

    ```c++
    if (foo) {
        bar();
    }
    ```

##### LambdaBodyIndentation

- `lambda` 主体的缩进样式。（默认）导致 `lambda` 主体相对于签名的缩进级别缩进一个额外的级别。`OuterScope` 强制 `lambda` 主体相对于包含 `lambda` 签名的父作用域缩进一个额外的级别

  - `Signature`：相对于 `lambda` 签名对齐 `lambda` 主体。这是默认设置

    ```c++
    someMethod(
        [](SomeReallyLongLambdaSignatureArgument foo) {
          return;
        });
    ```

  - `OuterScope`：相对于 `lambda` 签名所在的外部范围的缩进级别对齐 `lambda` 主体

    ```c++
    someMethod(
        [](SomeReallyLongLambdaSignatureArgument foo) {
      return;
    });
    ```

##### LineEnding

- 要使用的行尾样式（`\n`或`\r\n`）
  - `LF`：`\n`
  - `CRLF`：`\r\n`
  - `DeriveLF`：除非输入有更多以`\r\n`结尾的行，否则使用 `\n`
  - `DeriveCRLF`：与`DeriveLF`相反

##### MaxEmptyLinesToKeep

- 要保留的最大连续空行数

##### NamespaceIndentation

- 名称空间使用的缩进

  - `None`：不要在名称空间中缩进

    ```c++
    namespace out {
    int i;
    namespace in {
    int i;
    }
    }
    ```

  - `Inner`：只在内部名称空间中缩进(嵌套在其他名称空间中)

    ```c++
    namespace out {
    int i;
    namespace in {
        int i;
    }
    }
    ```

  - `All`： 缩进所有名称空间

    ```c++
    namespace out {
        int i;
        namespace in {
            int i;
        }
    }
    ```

##### PPIndentWidth

- 用于缩进预处理器语句的列数。 当设置为 -1（默认）时，`IndentWidth`也用于预处理器语句

  ```c++
  PPIndentWidth: 1
  
  #ifdef __linux__
  # define FOO
  #else
  # define BAR
  #endif
  ```

##### PackConstructorInitializers

- 要使用的包构造函数初始值设定项样式

  - `Never`：始终将每个构造函数初始化器放在自己的行上

    ```c++
    Constructor()
        : a(),
          b()
    ```

  - `BinPack`：Bin-pack 构造函数初始值设定项

    ```c++
    Constructor()
        : aaaaaaaaaaaaaaaaaaaa(), bbbbbbbbbbbbbbbbbbbb(),
          cccccccccccccccccccc()
    ```

  - `CurrentLine`：如果合适，将所有构造函数初始值设定项放在当前行。 否则，将每个都放在自己的行上

    ```c++
    Constructor() : a(), b()
    
    Constructor()
        : aaaaaaaaaaaaaaaaaaaa(),
          bbbbbbbbbbbbbbbbbbbb(),
          ddddddddddddd()
    ```

  - `NextLine`：与 `CurrentLine` 相同，但如果所有构造函数初始值设定项都不适合当前行，则尝试将它们放在下一行

    ```c++
    Constructor() : a(), b()
    
    Constructor()
        : aaaaaaaaaaaaaaaaaaaa(), bbbbbbbbbbbbbbbbbbbb(), ddddddddddddd()
    
    Constructor()
        : aaaaaaaaaaaaaaaaaaaa(),
          bbbbbbbbbbbbbbbbbbbb(),
          cccccccccccccccccccc()
    ```

  - `NextLineOnly`：如果合适，请将所有构造函数初始化器放在下一行。否则，把每一个放在单独的一行

    ```c++
    Constructor()
        : a(), b()
    
    Constructor()
        : aaaaaaaaaaaaaaaaaaaa(), bbbbbbbbbbbbbbbbbbbb(), ddddddddddddd()
    
    Constructor()
        : aaaaaaaaaaaaaaaaaaaa(),
          bbbbbbbbbbbbbbbbbbbb(),
          cccccccccccccccccccc()
    ```

##### PointerAlignment

- 指针和引用对齐样式

  - `Left`：将指针向左对齐

    ```c++
    int* a;
    ```

  - `Right`：将指针向右对齐

    ```c++
    int *a;
    ```

  - `Middle`：在中间对齐指针

    ```c++
    int * a;
    ```

##### RawStringFormats

- 定义在原始字符串中检测支持的语言代码块的提示

- 带有匹配的分隔符或包含匹配的函数名的原始字符串将根据 `.clang-format` 文件中定义的语言的样式进行重新格式化，假设该语言是指定的语言。如果在.`clang-format` 文件中没有为特定语言定义样式，则使用 [BasedOnStyle](https://tqfx.org/clang-format/BasedOnStyle) 给出的预定义样式。如果没有找到 [BasedOnStyle](https://tqfx.org/clang-format/BasedOnStyle)，则格式化基于 `llvm` 风格。匹配分隔符优先于匹配的封闭函数名，以确定原始字符串内容的语言。

- 如果指定了规范分隔符，同一语言中出现的其他分隔符将尽可能更新为规范。

- 每种语言最多应该有一个规范，每个分隔符和包围函数不应该出现在多个规范中。

- 要在 `.clang-format` 文件中配置它，请使用：

  ```c++
  RawStringFormats:
    - Language: TextProto
        Delimiters:
          - 'pb'
          - 'proto'
        EnclosingFunctions:
          - 'PARSE_TEXT_PROTO'
        BasedOnStyle: google
    - Language: Cpp
        Delimiters:
          - 'cc'
          - 'cpp'
        BasedOnStyle: llvm
        CanonicalDelimiter: 'cc'
  ```

##### ReferenceAlignment

- 引用对齐样式（覆盖引用的`PointerAlignment`）

  - `Pointer`：像`PointerAlignment`一样对齐引用

  - `Left`：将引用对齐到左侧

    ```c++
    int& a;
    ```

  - `Right`：将引用对齐到右侧

    ```c++
    int &a;
    ```

  - `Middle`：在中间对齐引用

    ```c++
    int & a;
    ```

##### ReflowComments

- 如果为 `true`，`clang-format` 将尝试重新输入注释

  - `true`：

    ```c++
    // veryVeryVeryVeryVeryVeryVeryVeryVeryVeryVeryLongComment with plenty of
    // information
    /* second veryVeryVeryVeryVeryVeryVeryVeryVeryVeryVeryLongComment with plenty of
    * information */
    ```

  - `false`：

    ```c++
    // veryVeryVeryVeryVeryVeryVeryVeryVeryVeryVeryLongComment with plenty of information
    /* second veryVeryVeryVeryVeryVeryVeryVeryVeryVeryVeryLongComment with plenty of information */
    ```

##### SeparateDefinitionBlocks

- 指定使用空行分隔定义块，包括类、结构、枚举和函数。
  - `Leave`：保持定义块不变
  - `Always`：在定义块之间插入空行
  - `Never`：删除定义块之间的任何空行

##### ShortNamespaceLines

- 短名称空间所包含的最大展开行数。默认为1。
- 这通过计算未包裹的行（即既不包含打开也不包含关闭的命名空间大括号）来确定短命名空间的最大长度，并使`FixNamespaceComments`省略为这些行添加结束注释。

##### SortIncludes

- 控制`clang-format`是否以及如何对`#includes`进行排序。

  - `Never`：包含永远不会排序

    ```c++
    #include "B/A.h"
    #include "A/B.h"
    #include "a/b.h"
    #include "A/b.h"
    #include "B/a.h"
    ```

  - `CaseSensitive`：`include` 以大小写敏感的方式排序

    ```c++
    #include "A/B.h"
    #include "A/b.h"
    #include "B/A.h"
    #include "B/a.h"
    #include "a/b.h"
    ```

  - `CaseInsensitive`：`include` 以不区分字母或大小写的方式排序

    ```c++
    #include "A/B.h"
    #include "A/b.h"
    #include "a/b.h"
    #include "B/A.h"
    #include "B/a.h"
    ```

##### SortUsingDeclarations

- 如果为 `true`，`clang-format` 将使用声明进行排序

  - `Never`：使用声明从不排序

    ```c++
    using std::chrono::duration_cast;
    using std::move;
    using boost::regex;
    using boost::regex_constants::icase;
    using std::string;
    ```

  - `Lexicographic`：使用声明的顺序如下：按`::`拆分字符串并丢弃任何初始空字符串。按字母顺序对名称列表进行排序，在这些组中，名称的字母顺序不区分大小写。

    ```c++
    using boost::regex;
    using boost::regex_constants::icase;
    using std::chrono::duration_cast;
    using std::move;
    using std::string;
    ```

  - `LexicographicNumeric`：使用声明的顺序如下：按`::`拆分字符串并丢弃任何初始空字符串。每个列表的最后一个元素是一个非命名空间名称；其他都是命名空间名称。按字母顺序对名称列表进行排序，其中单个名称的排序顺序是所有非名称空间名称都在所有名称空间名称之前，在这些组中，名称的字母顺序不区分大小写。

    ```c++
    using boost::regex;
    using boost::regex_constants::icase;
    using std::move;
    using std::string;
    using std::chrono::duration_cast;
    ```

##### SpaceAfterCStyleCast

- 如果为 `true`，则在 `C` 风格强制转换后插入一个空格

  - `true`：

    ```c++
    (int) i;
    ```

  - `false`：

    ```c++
    (int)i;
    ```

##### SpaceAfterLogicalNot

- 如果为 `true`，则在逻辑否操作符(`!`)后面插入一个空格

  - `true`：

    ```c++
    ! someExpression();
    ```

  - `false`：

    ```c++
    !someExpression();
    ```

##### SpaceAfterTemplateKeyword

- 如果为 `true`，则在 `template` 关键字后面插入一个空格

  - `true`：

    ```c++
    template <int> void foo();
    ```

  - `false`：

    ```c++
    template<int> void foo();
    ```

##### SpaceAroundPointerQualifiers

- 定义在何种情况下在指针限定符之前或之后放置空格

  - `Default`：不要确保指针限定符周围有空格，而是使用`PointerAligation`

    ```c++
    PointerAlignment: Left                 PointerAlignment: Right
    void* const* x = NULL;         vs.     void *const *x = NULL;
    ```

  - `Before`：确保在指针限定符之前有空格

    ```c++
    PointerAlignment: Left                 PointerAlignment: Right
    void* const* x = NULL;         vs.     void * const *x = NULL;
    ```

  - `After`： 确保在指针限定符后有空格

    ```c++
    PointerAlignment: Left                 PointerAlignment: Right
    void* const * x = NULL;         vs.    void *const *x = NULL;
    ```

  - `Both`：确保在指针限定符的前后都有空格

    ```c++
    PointerAlignment: Left                 PointerAlignment: Right
    void* const * x = NULL;         vs.    void * const *x = NULL;
    ```

##### SpaceBeforeAssignmentOperators

- 如果为 `false`，则在赋值操作符之前删除空格

  - `true`：

    ```c++
    int a = 5;
    a += 42;
    ```

  - `false`：

    ```c++
    int a= 5;
    a+= 42;
    ```

##### SpaceBeforeCaseColon

- 如果为 `false`，则在 `case` 冒号之前删除空格

  - `true`：

    ```c++
    switch (x) {
    case 1 : break;
    }
    ```

  - `false`：

    ```c++
    switch (x) {
    case 1: break;
    }
    ```

##### SpaceBeforeCpp11BracedList

- 如果为 `true`，则在用于初始化对象的 `C++11` 大括号列表之前插入一个空格(在前面的标识符或类型之后)

  - `true`：

    ```c++
    Foo foo { bar };
    Foo {};
    vector<int> { 1, 2, 3 };
    new int[3] { 1, 2, 3 };
    ```

  - `false`：

    ```c++
    Foo foo { bar };
    Foo {};
    vector<int> { 1, 2, 3 };
    new int[3] { 1, 2, 3 };
    ```

##### SpaceBeforeCtorInitializerColon

- 如果为 `false`，在构造函数初始化器冒号之前的空格将被删除

  - `true`：

    ```c++
    Foo::Foo() : a(a) {}
    ```

  - `false`：

    ```c++
    Foo::Foo(): a(a) {}
    ```

##### SpaceBeforeInheritanceColon

- 如果为 `false`，在继承冒号之前的空格将被删除

  - `true`：

    ```c++
    class Foo : Bar {}
    ```

  - `false`：

    ```c++
    class Foo: Bar {}
    ```

##### SpaceBeforeParens

- 定义在何种情况下在开括号前放空格

  - `Never`：不要在括号前放空格

    ```c++
    void f() {
        if(true) {
            f();
        }
    }
    ```

  - `ControlStatements`：只在控制语句关键字(`for`/`if`/`while`...)之后的开括号前放一个空格

    ```c++
    void f() {
        if (true) {
            f();
        }
    }
    ```

  - `ControlStatementsExceptControlMacros`：与 `ControlStatements` 相同，除了这个选项不适用于 [ForEach](https://tqfx.org/clang-format/ForEach) 宏。这在 [ForEach](https://tqfx.org/clang-format/ForEach) 宏被视为函数调用而不是控制语句的项目中非常有用

    ```c++
    void f() {
        Q_FOREACH(...) {
            f();
        }
    }
    ```

  - `NonEmptyParentheses`：只有括号不是空的时候才在括号前放一个空格，即 `()`

    ```c++
    void() {
        if (true) {
            f();
            g (x, y, z);
        }
    }
    ```

  - `Always`：总是在开括号前放一个空格，除非语法规则禁止(在类似函数的宏定义中)或由其他风格规则决定(在一元操作符、开括号后，等等)

    ```c++
    void f () {
        if (true) {
            f ();
        }
    }
    ```

  - `Custom`：在`SpaceBforeParensOptions`中配置括号前的每个单独空格

##### SpaceBeforeParensOptions

- 控制括号前的单个空格，如果`SpaceBeforeParens`设置为 `Custom`，则使用它来指定应如何处理括号大小写前的每个单独的空格。否则，这将被忽略

  ```c++
  SpaceBeforeParens: Custom
  SpaceBeforeParensOptions:
    AfterControlStatements: true
    AfterFunctionDefinitionName: true
  Nested configuration flags:
  ```

  - **AfterControlStatements** ：如果为 `true`，则在控制语句关键字（`for`/`if`/`while`...）和左括号之间放置空格

    ```c++
    true:                                  false:
    if (...) {}                     vs.    if(...) {}
    ```

  - **AfterForeachMacros**：如果为 `true`，则在 `foreach` 宏和左括号之间放置空格

    ```c++
    true:                                  false:
    FOREACH (...)                   vs.    FOREACH(...)
      <loop-body>                            <loop-body>
    ```

  - **AfterFunctionDeclarationName**：如果为 `true`，则在函数声明名称和左括号之间放置一个空格

    ```c++
    true:                                  false:
    void f ();                      vs.    void f();
    ```

  - **AfterFunctionDefinitionName**：如果为 `true`，则在函数定义名称和左括号之间放置一个空格

    ```c++
    true:                                  false:
    void f () {}                    vs.    void f() {}
    ```

  - **AfterIfMacros**：如果为 `true`，则在 `if` 宏和左括号之间放置空格

    ```c++
    true:                                  false:
    IF (...)                        vs.    IF(...)
      <conditional-body>                     <conditional-body>
    ```

  - **BeforeNonEmptyParentheses**：如果为 `true`，则仅当括号不为空时才在括号前放置一个空格

    ```c++
    true:                                  false:
    void f (int a);                 vs.    void f();
    f (a);                                 f();
    ```

##### SpaceBeforeRangeBasedForLoopColon

- 如果为 `false`，在基于范围的 `for loop` 冒号之前将删除空格

  - `true`：

    ```c++
    for (auto v : values) {}
    ```

  - `false`：

    ```c++
    for(auto v: values) {}
    ```

##### SpaceBeforeSquareBrackets

- 如果为 `true`，空格将在 `[` 之前。不受影响。只有第一个 `[` 会被加一个空格

  - `true`：

    ```c++
    int a [5];
    int a [5][5];
    ```

  - `false`：

    ```c++
    int a[5];
    int a[5][5];
    ```

##### SpaceInEmptyBlock

- 如果为 `true`，将在 `{}` 中插入空格

  - `true`：

    ```c++
    void f() { }
    while (true) { }
    ```

  - `false`：

    ```c++
    void f() {}
    while (true) {}
    ```

##### SpaceInEmptyParentheses

- 如果为 `true`，可以在 `()` 中插入空格

  - `true`：

    ```c++
    void f( ) {
        int x[] = {foo( ), bar( )};
        if (true) {
            f( );
        }
    }
    ```

  - `false`：

    ```c++
    void f() {
        int x[] = {foo(), bar()};
        if (true) {
            f();
        }
    }
    ```

##### SpacesBeforeTrailingComments

- 尾行注释(`//` -注释)之前的空格数，这不会影响末尾的块注释(`/*` -注释)，因为这些注释通常有不同的使用模式和一些特殊情况

  ```c++
  SpacesBeforeTrailingComments: 3
  void f() {
    if (true) {   // foo1
      f();        // bar
    }             // foo
  }
  ```

##### SpacesInAngles

- 用于模板参数列表的 `SpacesInAnglesStyle`

  - `Never`：删除 `<` 之后和 `>` 之前的空格

    ```c++
    static_cast<int>(arg);
    std::function<void(int)> fct;
    ```

  - `Always`：在 `<` 之后和 `>` 之前添加空格

    ```c++
    static_cast< int >(arg);
    std::function< void(int) > fct;
    ```

  - `Leave`：如果存在空格，则在 `<` 之后和之前保留一个空格。 选项标准：`Cpp03` 优先

##### SpacesInCStyleCastParentheses

- 如果为 `true`，则可以在 `C` 风格的强制转换中插入空格

  - `true`：

    ```c++
    x = ( int32 )y
    ```

  - `false`：

    ```c++
    x = (int32)y
    ```

##### SpacesInConditionalStatement

- 如果为 `true`，则在 `if`/`for`/`switch`/`while` 条件周围插入空格

  - `true`：

    ```c++
    if ( a )  { ... }
    while ( i < 5 )  { ... }
    ```

  - `false`：

    ```c++
    if (a) { ... }
    while (i < 5) { ... }
    ```

##### SpacesInContainerLiterals

- 如果为 `true`，则在容器字面量(例如 `ObjC` 和 `Javascript` 数组和 `dict` 字面量)中插入空格

  - `true`：

    ```c++
    var arr = [ 1, 2, 3 ];
    f({a : 1, b : 2, c : 3});
    ```

  - `false`：

    ```c++
    var arr = [1, 2, 3];
    f({a: 1, b: 2, c: 3});
    ```

##### SpacesInLineCommentPrefix

- 一行注释的开头允许有多少个空格。要禁用最大值，请将其设置为 `-1`，但最大值优先于最小值

  ```c++
  Minimum = 1 Maximum = -1 // 强制输入一个空格
  
  // 但是更多的空间是可能的
  
  Minimum = 0 Maximum = 0 //强制每个注释直接在斜杠后面开始
  ```

- 请注意，在行注释部分，后续行的相对缩进被保留，这意味着如下：

  ```c++
  before:                                   after:
  Minimum: 1
  //if (b) {                                // if (b) {
  //  return true;                          //   return true;
  //}                                       // }
  
  Maximum: 0
  /// List:                                 ///List:
  ///  - Foo                                /// - Foo
  ///    - Bar                              ///   - Bar
  ```

- 只有当`ReflowComments`设置为`true`时，选项才有效

- 嵌套的配置标记：

  - `Minimum` 注释开始处的最小空格数。
  - `Maximum` 注释开始处的最大空格数。

##### SpacesInParens

- 定义在哪些情况下将在后面`(`和前面`)`插入空格

  - `Never`：在括号内不加空格

    ```c++
    void f() {
      if(true) {
        f();
      }
    }
    ```

  - `Custom`：在`SpacesInParensOptions`的括号中配置每个单独的空格

##### SpacesInParensOptions

- 括号中单个空格的控制，如果`SpacesInParens`设置为“自定义”，则使用此选项指定如何处理括号大小写中的每个单独空格。否则，这将被忽略

  ```c++
  # Should be declared this way:
  SpacesInParens: Custom
  SpacesInParensOptions:
    InConditionalStatements: true
    Other: true
  ```

  - `InConditionalStatements`：仅在条件语句（`for/if/while/switch…`）内的括号中放一个空格

    ```c++
    true:                                  false:
    if ( a )  { ... }              vs.     if (a) { ... }
    while ( i < 5 )  { ... }               while (i < 5) { ... }
    ```

  - `InCStyleCasts`：在C样式转换中放置空格

    ```c++
    true:                                  false:
    x = ( int32 )y                 vs.     x = (int32)y
    ```

  - `InEmptyParentheses`：仅当括号为空时，才在括号中加空格，即`()`

    ```c++
    true:                                false:
    void f( ) {                    vs.   void f() {
      int x[] = {foo( ), bar( )};          int x[] = {foo(), bar()};
      if (true) {                          if (true) {
        f( );                                f();
      }                                    }
    }                                    }
    ```

  - `Other`：在前面选项未涵盖的括号中放一个空格

    ```c++
    true:                                  false:
    t f( Deleted & ) & = delete;   vs.     t f(Deleted &) & = delete;
    ```

##### SpacesInSquareBrackets

- 如果为 `true`，将在 `[` 和之前 `]` 后面插入空格。没有参数或未指定大小的数组声明的匿名函数将不受影响

  - `true`：

    ```c++
    int a[ 5 ];
    std::unique_ptr<int[]> foo() {} // Won't be affected
    ```

  - `false`：

    ```c++
    int a[5];
    ```

##### Standard

- 解析和格式化与这个标准兼容的 `C++` 结构

  ```c++
  c++03:                                 latest:
  vector<set<int> > x;           vs.     vector<set<int>> x;
  ```

  - `c++03`：解析并格式化为C++03。`Cpp03`是`c++03`的弃用别名
  - `c++11`：解析并格式化为C++11
  - `c++14`：解析并格式化为C++14
  - `c++17`：解析并格式化为C++17
  - `c++20`：解析并格式化为C++20
  - `Latest`：使用最新支持的语言版本进行解析和格式化。`Cpp11`是`Latest`的弃用别名
  - `Auto`：基于输入自动检测

##### StatementAttributeLikeMacros

- 在语句前面被忽略的宏，就像它们是一个属性一样。这样它们就不会被解析为标识符，例如Qt的emit

  ```c++
  AlignConsecutiveDeclarations: true
  StatementAttributeLikeMacros: []
  unsigned char data = 'x';
  emit          signal(data); // This is parsed as variable declaration.
  
  AlignConsecutiveDeclarations: true
  StatementAttributeLikeMacros: [emit]
  unsigned char data = 'x';
  emit signal(data); // Now it's fine again.
  ```

##### StatementMacros

- 宏的一个列表，应该被解释为完整的语句。典型的宏是表达式，需要添加分号;有时情况并非如此，这允许 `clang-format` 能够识别这种情况。例如: `Q_UNUSED`

##### TabWidth

- 用于制表位的列数

##### TypeNames

- 应被解释为类型名的非关键字标识符的列表，类型名称和另一个非关键字标识符之间的*、&或&&被注释为指针或引用标记，而不是二进制运算符

##### TypenameMacros

- 宏的一个列表，它应该被解释为类型声明而不是函数调用，这些应该是以下形式的宏：

  ```c++
  STACK_OF(...)
  ```

- 在 `.clang-format` 配置文件中，可以这样配置：

  ```c++
  TypenameMacros: ['STACK_OF', 'LIST']
  ```

- 例如: `OpenSSL STACK_OF`, `BSD LIST_ENTRY`

##### UseTab

- 在结果文件中使用制表符
  - `Never`：从不使用制表符
  - `ForIndentation`：仅在缩进时使用制表符
  - `ForContinuationAndIndentation`：用制表符填充所有的前导空格，并在一行中使用空格进行对齐(例如连续的赋值和声明)
  - `AlignWithSpaces`：使用制表符进行行延续和缩进，使用空格进行对齐
  - `Always`：当我们需要填补至少从一个制表位到下一个制表位的空白时，使用制表位

##### WhitespaceSensitiveMacros

- 一个对空格敏感且不应被触碰的宏列表，这些应该是以下形式的宏：

  ```c++
  STRINGIZE(...)
  ```

- 在 `.clang-format` 配置文件中，可以这样配置：

  ```c++
  WhitespaceSensitiveMacros: ['STRINGIZE', 'PP_STRINGIZE']
  ```

- 例如: `BOOST_PP_STRINGIZE`