# cxx的二进制文件  
这在未来还有改变的可能  
  
cxx_binary() 规则可以将 C/C++ 源文件和其依赖构建成一个二进制可执行文件。如果 C/C++ 的依赖库是链式的，那么所生成的本地可执行程序将链接其的静态链接库（一种不使用 [PIC](https://en.wikipedia.org/wiki/Position-independent_code) 的方式）。  
  
## 参数  
  
■ `name`（这个参数是必需的）规则的名称。  
  
■ `srcs`（默认为 [ ] ）整套 C、c++ ，汇编源文件预处理,编译,装配都遵循这个规则。我们基于它们的文件扩展名确定哪些阶段运行在哪个输入源，看GCC文档在如何解读文件扩展名上的更多细节。每个元素可以是一个字符串指定源文件(如 ‘foo / bar.c’ )或一个元组的字符串指定源文件和编译标志（如 （'foo / bar.c ',[' - wall ',' -Werror ']））。预处理和编译该文件时，除了规定的其他标记，这种规定的标记作为后一种情况是可以被使用的（若适用）
  
■ `platform_srcs`（默认为 [ ] ）平台特定的源文件。这些应该指定为一组对,第一个元素是一个平台名称匹配的，不违反安全性的正则化表达式（在 java.util.regex.Pattern syntax 包中）。第二个元素不是源文件的列表就是元组的源文件的列表和列表编译标记，如果平台与正则表达式相匹配就去预处理、编译和组装。  
  
■ `header_namespace`（默认为 `name` ）当包括标题这一目标路径前缀。默认为目标的名称。可以包含斜杠(/),但不能从一开始就使用。有关更多信息,请参见`headers`。  
  

■ `preprocessor_flags`（默认为 [ ] ）当预处理任何上述来源时标记使用(需要预处理)。  
  
■ `platform_preprocessor_flags`（默认为 [ ] ）平台特定的预处理器标记。这些应该指定为一组对,第一个元素是一个平台名称匹配的，不违反安全性的正则化表达式（在 java.util.regex.Pattern syntax 包中）。第二个元素是列表标记，当预处理目标的来源时使用。有关更多信息,请参见`preprocessor_flags`。  
  
■ `compiler_flags`（默认为 [ ] ）当编译任何上述来源时标记使用(需要预处理)。  
  
■ `platform_compiler_flags`（默认为 [ ] ）平台特定的编译器标志。这些应该指定为一组对,第一个元素是一个平台名称匹配的，不违反安全性的正则化表达式（在 java.util.regex.Pattern syntax 包中）。第二个元素是列表标记，当编译目标的来源时使用。有关更多信息,请参见`compiler_flags`。  
  
■ `linker_flags`（默认为 [ ] ）无论这个规则是否包络一个连接操作都标记使用（比如链接进一个可执行程序或共享库）。  
  
■ `platform_linker_flags `（默认为 [ ] ）平台特定的编译器标志。这些应该指定为一组对,第一个元素是一个平台名称匹配的，不违反安全性的正则化表达式（在 java.util.regex.Pattern syntax 包中）。第二个元素是列表标记，当这个目标包含一个连接操作时使用。有关更多信息,请参见`linker_flagss`。  
  
■ `link_style`（默认为 `static`）决定是否建立并且静态或动态链接这个二进制文件的依赖关系。可以是 `static` 或 `dynamic` 的。  
  
■ `tests`（默认为 [ ] ）确定执行此目标的测试规则的生成目标列表。
  
■ `visibility `（默认为 [ ] ）确定构建规则的目标模式列表,可以包括`deps`这个规则。  
  
##例子    
    

````
# A rule that builds a C/C++ native executable from a single .cpp file
# its corresponding header, and a C/C++ library dependency.
cxx_binary(
  name = 'echo',
  srcs = [
    'echo.cpp',
  ],
  headers = [
    'echo.h',
  ],
  deps = [
    ':util',
  ],
)

cxx_library(
  name = 'util',
  srcs = [
    'util.cpp',
  ],
  headers = [
    'util.h',
  ],
)
````

