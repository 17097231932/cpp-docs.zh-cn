---
title: "字符串和字符文本 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "R"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "转义序列"
  - "L 常量"
  - "字符串"
  - "字符串, C++"
  - "Null 字符串"
  - "Null 字符串, 以 null 结尾的字符串"
  - "NULL, 字符常量"
  - "字符串"
  - "字符串, 语法"
  - "字符串 [C++], 字符串"
  - "宽字符, 字符串"
ms.assetid: 61de8f6f-2714-4e7b-86b6-a3f885d3b9df
caps.latest.revision: 36
caps.handback.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 字符串和字符文本 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 支持各种字符串和字符类型，并提供表示每种类型的文本值的方法。 在源代码中，使用字符集表示字符和字符串文本的内容。 通用字符名称和转义字符允许你仅使用基本源字符集表示任何字符串。 原始字符串使你可以避免使用转义字符，可以用于表示所有类型的字符串。 你还可以创建 std::string 文本，而无需执行额外的构造或转换步骤。  
  
```cpp  
#include <string> using namespace std::string_literals; // enables s-suffix for std::string literals int main() { // Character literals auto c0 =   'A'; // char auto c1 = u8'A'; // char auto c2 =  L'A'; // wchar_t auto c3 =  u'A'; // char16_t auto c4 =  U'A'; // char32_t // String literals auto s0 =   "hello"; // const char* auto s1 = u8"hello"; // const char*, encoded as UTF-8 auto s2 =  L"hello"; // const wchar_t* auto s3 =  u"hello"; // const char16_t*, encoded as UTF-16 auto s4 =  U"hello"; // const char32_t*, encoded as UTF-32 // Raw string literals containing unescaped \ and " auto R0 =   R"("Hello \ world")"; // const char* auto R1 = u8R"("Hello \ world")"; // const char*, encoded as UTF-8 auto R2 =  LR"("Hello \ world")"; // const wchar_t* auto R3 =  uR"("Hello \ world")"; // const char16_t*, encoded as UTF-16 auto R4 =  UR"("Hello \ world")"; // const char32_t*, encoded as UTF-32 // Combining string literals with standard s-suffix auto S0 =   "hello"s; // std::string auto S1 = u8"hello"s; // std::string auto S2 =  L"hello"s; // std::wstring auto S3 =  u"hello"s; // std::u16string auto S4 =  U"hello"s; // std::u32string // Combining raw string literals with standard s-suffix auto S5 =   R"("Hello \ world")"s; // std::string from a raw const char* auto S6 = u8R"("Hello \ world")"s; // std::string from a raw const char*, encoded as UTF-8 auto S7 =  LR"("Hello \ world")"s; // std::wstring from a raw const wchar_t* auto S8 =  uR"("Hello \ world")"s; // std::u16string from a raw const char16_t*, encoded as UTF-16 auto S9 =  UR"("Hello \ world")"s; // std::u32string from a raw const char32_t*, encoded as UTF-32 }  
```  
  
 字符串文本可以米有前缀，也可以具有 `u8`、`L`、`u` 和 `U` 前缀以分别指示窄字符（单字节或多字节）、UTF\-8、宽字符（UCS\-2 或 UTF\-16）、UTF\-16 和 UTF\-32 编码。 原始字符串文本可以具有 `R``u8R`、`LR`、`uR` 和 `UR` 前缀来表示这些编码的原始版本等效项。  若要创建临时或静态 std::string 值，可以使用带 `s` 后缀的字符串文本或原始字符串文本。 有关详细信息，请参阅下面的“字符串文本”一节。 有关基本源字符集、通用字符名称以及在源代码中使用扩展代码页中的字符的详细信息，请参阅[字符集](../cpp/character-sets2.md)。  
  
## 字符文本  
 *字符文本*由一个字符常量构成。 它由用单引号引起来的字符表示。 有四种类型的字符文本：  
  
-   类型 `char` 的窄字符文本，例如 `'a'`  
  
-   类型 `wchar_t` 的宽字符文本，例如 `L'a'`  
  
-   类型 `char16_t` 的宽字符文本，例如 `u'a'`  
  
-   类型 `char32_t` 的宽字符文本，例如 `U'a'`  
  
 用于字符文本的字符可以是除保留字符反斜杠 \('\\'\)、单引号 \('\) 和换行符以外的任何字符。 可以使用转义序列指定保留字符。 可以通过使用通用字符名称指定字符，只要类型的大小足以保留字符。  
  
###  <a name="bkmk_Escape"></a> 转义序列  
 有三种类型的转义序列：简单、八进制和十六进制。 转义序列可以是以下任一项：  
  
|值|转义序列|值|转义序列|  
|-------|----------|-------|----------|  
|换行符|\\n|反斜杠|\\\\|  
|水平制表符|\\t|问号|? 或 \\?|  
|垂直制表符|\\v|单引号|\\'|  
|退格符|\\b|双引号|\\"|  
|回车符|\\r|null 字符|\\0|  
|换页符|\\f|八进制|\\ooo|  
|警报（响铃）|\\a|十六进制|\\xhhh|  
  
 以下代码演示使用窄字符文本的转义字符的一些示例。 相同语法对于其他字符串文本类型有效。  
  
```cpp  
#include <iostream> using namespace std; int main() { char newline = '\n'; char tab = '\t'; char backspace = '\b'; char backslash = '\\'; char nullChar = '\0'; cout << "Newline character: " << newline << "ending" << endl; // Newline character: //  ending cout << "Tab character: " << tab << "ending" << endl; // Tab character : ending cout << "Backspace character: " << backspace << "ending" << endl; // Backspace character : ending cout << "Backslash character: " << backslash << "ending" << endl; // Backslash character : \ending cout << "Null character: " << nullChar << "ending" << endl; //Null character:  ending }  
```  
  
 **Microsoft 专用**  
  
 为了从没有前缀的字符文本创建字，编译器将单引号之间的字符或字符序列转换为 32 位整数内的 8 位值。 文本中的多个字符根据需要从高序位到低序位填充相应字节。 为了创建 `char` 值，编译器采用低序位字节。 为了创建 `wchar_t` 或  `char16_t` 值，编译器采用低序位字。 如果在分配的字节或字上设置了任何位，则编译器会警告结果被截断。  
  
```cpp  
char c0    = 'abcd';    // C4305, C4309, truncates to 'd' wchar_t w0 = 'abcd';    // C4305, C4309, truncates to '\x6364'  
```  
  
 八进制转义序列包含一个反斜杠，后跟最多 3 个八进制数字的序列。 对于将包含超过三位数字的八进制转义序列，其行为被视为三位数八进制序列，之后的数字被视为字符，这可能导致令人惊讶的结果。 例如：  
  
```cpp  
char c1 = '\100';   // '@' char c2 = '\1000';  // C4305, C4309, truncates to '0'   
```  
  
 对于将包含非八进制字符的转义序列，其求值结果为全部由八进制字符组成的八进制序列，后跟剩余字符。 例如：  
  
```cpp  
char c3 = '\009';   // '9' char c4 = '\089';   // C4305, C4309, truncates to '9' char c5 = '\qrs';   // C4129, C4305, C4309, truncates to 's'  
```  
  
 十六进制转义序列包含一个反斜杠，后跟字符 `x` 和一个十六进制数字序列。 不包含十六进制数字的转义序列将导致编译器错误 C2153：“十六进制文本必须至少有一个十六进制数字”。 将忽略前导零。 对于将具有十六进制和非十六进制字符的转义序列，其求值结果为全部由十六进制字符组成的十六进制转义序列，后跟非十六进制字符。   在没有前缀或使用 u8 前缀的窄字符文本中，最大的十六进制值为 0xFF。 在使用 L 或 u 前缀的宽字符文本中，最大的十六进制值为 0xFFFF。 在使用 U 前缀的宽字符文本中，最大的十六进制值为 0xFFFFFFFF。  
  
```cpp  
char c6 = '\x0050'; // 'P' char c7 = '\x0pqr'; // C4305, C4309, truncates to 'r'  
```  
  
 如果以 `L` 为前缀的宽字符文本包含多个字符，则从第一个字符中获取值。 将忽略后续字符，这不同于没有前缀的等效窄字符文本的行为。  
  
```cpp  
wchar_t w1 = L'\100';   // L'@' wchar_t w2 = L'\1000';  // C4066 L'@', 0 ignored wchar_t w3 = L'\009';   // C4066 L'\0', 9 ignored wchar_t w4 = L'\089';   // C4066 L'\0', 89 ignored wchar_t w5 = L'\qrs';   // C4129, C4066 L'q' escape, rs ignored wchar_t w6 = L'\x0050'; // L'P' wchar_t w7 = L'\x0pqr'; // C4066 L'\0', pqr ignored  
```  
  
 **结束 Microsoft 专用**  
  
 反斜杠字符 \(\\\) 在位于行末尾时将作为行继续符。 如果你希望反斜杠字符显示为字符文本，则必须在一行中键入两个反斜杠 \(`\\`\)。 有关行继续符的详细信息，请参阅[转换阶段](../preprocessor/phases-of-translation.md)。  
  
###  <a name="bkmk_UCN"></a> 通用字符名称  
 在字符文本和本机（非原始）字符串文本中，任何字符都可由通用字符名称表示。  通用字符名称由前缀 \\U 后跟八位数 Unicode 码位组成，或者由前缀 \\u 后跟四位数 Unicode 码位组成。 必须分别显示所有八个或四个数字，以组成一个格式正确的通用字符名称。  
  
```cpp  
char u1 = 'A';          // 'A' char u2 = '\101';       // octal, 'A' char u3 = '\x41';       // hexadecimal, 'A' char u4 = '\u0041';     // \u UCN 'A' char u5 = '\U00000041'; // \U UCN 'A'  
```  
  
 **代理项对**  
  
 通用字符名称不能对代理项码位范围 D800\-DFFF 内的值进行编码。 对于 Unicode 代理项对，通过使用 `\UNNNNNNNN`（其中，NNNNNNNN 是字符的八位数码位）指定通用字符名称。 如果需要，编译器将生成一个代理项对。  
  
 在 C\+\+03 中，语言只允许字符串子集通过其通用字符名称来表示，并且允许某些实际不表示任何有效 Unicode 字符的通用字符名称。 这在 C\+\+11 标准中进行了修复。 在 C\+\+ 11 中，字符以及字符串文本和标识符可以使用通用字符名称。  有关通用字符名称的详细信息，请参阅[字符集](../cpp/character-sets2.md)。 有关 Unicode 的详细信息，请参阅 [Unicode](http://msdn.microsoft.com/library/dd374081\(v=vs.85\).aspx)。 有关代理项对的详细信息，请参阅[代理项对与补充字符](http://msdn.microsoft.com/library/dd374069\(v=vs.85\).aspx)。  
  
## 字符串文本  
 字符串文本表示字符序列，这些字符合起来可组成以 null 结尾的字符串。 字符必须放在双引号之间。 字符串文本有以下类型：  
  
### 窄字符串文本  
 窄字符串文本是一个没有前缀且以双引号分隔、以 null 结尾的 `const` `char`\[`n`\] 类型的数组，其中 n 是数组的长度（以字节为单位）。 窄字符串文本可包含除双引号 \(`"`\)、反斜杠 \(`\`\) 或换行符以外的所有图形字符。 窄字符串文本还可包含上面列出的转义序列和装入一个字节中的通用字符名称。  
  
```cpp  
const char *narrow = "abcd"; // represents the string: yes\no const char *escaped = "yes\\no";  
```  
  
 **UTF\-8 编码的字符串**  
  
 UTF\-8 编码的字符串是一个前缀为 u8 且以双引号分隔、以 null 结尾的 `const``char`\[`n`\] 类型的数组，其中 n 是编码的数组的长度（以字节为单位）。 以 u8 为前缀的字符串文本可包含除双引号 \(`"`\)、反斜杠 \(`\`\) 或换行符以外的所有图形字符。 以 u8 为前缀的字符串文本还可包含上面列出的转义序列和任何通用字符名称。  
  
```cpp  
const char* str1 = u8"Hello World"; const char* str2 = u8"\U0001F607 is O:-)";  
```  
  
### 宽字符串文本  
 宽字符串是一个以 null 结尾且具有前缀“`L`”的常数 `wchar_t` 数组，其中包含除双引号 \("\)、反斜杠 \(\\\) 或换行符以外的所有图形字符。 宽字符串文本可包含上面列出的转义序列和任何通用字符名称。  
  
```cpp  
const wchar_t* wide = L"zyxw"; const wchar_t* newline = L"hello\ngoodbye";  
```  
  
 **char16\_t 和 char32\_t \(C\+\+11\)**  
  
 C\+\+11 引入了可移植的 `char16_t`（16 位 Unicode）和 `char32_t`（32 位 Unicode）字符类型：  
  
```cpp  
auto s3 = u"hello"; // const char16_t* auto s4 = U"hello"; // const char32_t*  
```  
  
### 原始字符串 \(C\+\+11\)  
 原始字符串是一个以 null 结尾的数组（属于任何字符类型），其中包括含双引号 \("\)、反斜杠 \(\\\) 或换行符在内的所有图形字符。 原始字符串通常用于使用字符类的正则表达式，还用于 HTML 字符串和 XML 字符串。 有关示例，请参阅以下文章：[关于 C\+\+11 的 Bjarne Stroustrup 常见问题](http://go.microsoft.com/fwlink/?LinkId=401172)。  
  
```cpp  
// represents the string: An unescaped \ character const char* raw_narrow = R"(An unescaped \ character)"; const wchar_t* raw_wide = LR"(An unescaped \ character)"; const char*       raw_utf8  = u8R"(An unescaped \ character)"; const char16_t* raw_utf16 = uR"(An unescaped \ character)"; const char32_t* raw_utf32 = UR"(An unescaped \ character)";  
```  
  
 分隔符是用户定义的最多包含 16 个字符的序列，它紧贴在原始字符串文本的左括号之前，紧跟在右括号之后。  例如，在 `R"abc(Hello"\()abc"` 中，分隔符序列为 `abc`，字符串内容为 `Hello"\(`。 你可使用分隔符来消除同时含有双引号和括号的原始字符串。 这将导致编译器错误：  
  
```cpp  
// meant to represent the string: )” const char* bad_parens = R"()")";  // error C2059  
```  
  
 但分隔符能够解决这样的错误：  
  
```cpp  
const char* good_parens = R"xyz()")xyz";  
```  
  
 你可以构造在源中有换行的原始字符串文本（非转义字符）：  
  
```cpp  
// represents the string: hello //goodbye const wchar_t* newline = LR"(hello goodbye)";  
```  
  
### std::string 文本 \(C\+\+14\)  
 std::string 文本是用户定义的文本（请参阅下文）的标准库实现，表示为 "xyx"s（具有 `s` 后缀）。 这种类型的字符串会生成 std::string、std::wstring、std::u32string 或 std::u16string 类型的临时对象，具体取决于指定的前缀。 如上所示不使用任何前缀时，会生成 std::string。 L"xyz"s 生成 std::wstring。 u"xyz"s 生成 [std::u16string](../Topic/u16string.md)，而 U"xyz"s 生成 [std::u32string](../Topic/u32string.md)。  
  
```cpp  
//#include <string> //using namespace std::string_literals; string str{ "hello"s }; string str2{ u8"Hello World" }; wstring str3{ L"hello"s }; u16string str4{ u"hello"s }; u32string str5{ U"hello"s };  
```  
  
 s 后缀也可以用于原始字符串：  
  
```cpp  
u32string str6{ UR"(She said "hello.")"s };  
```  
  
 std::string 文本在 \<string\> 头文件的命名空间 `std::literals::string_literals` 中定义。 因为 `std::literals::string_literals` 和 `std::literals` 都声明为[内联命名空间](../cpp/namespaces-cpp.md)，所以会自动将 `std::literals::string_literals` 视为如同它直接属于命名空间 `std`。  
  
### 字符串文本大小  
 对于 ANSI char\* 字符串和其他单字节编码（不是 UTF\-8），字符串的大小（以字节为单位）是字符数加 1（用于 null 终止字符）。 对于所有其他字符串类型，大小不与字符数严格相关。 UTF\-8 使用最多四个 char 元素对某些*“代码单位”*进行编码，编码为 UTF\-16 的 char16\_t 或 wchar\_t 可以使用两个元素（针对总共四个字节）对单个*“代码单位”*进行编码。   本示例演示了宽字符串文本的大小（以字节为单位）：  
  
```cpp  
const wchar_t* str = L"Hello!"; const size_t byteSize = (wcslen(str) + 1) * sizeof(wchar_t);  
```  
  
 请注意，`strlen()` 和 `wcslen()` 不包括 null 终止字符的大小，该字符的大小等于字符串类型的元素大小：char\* 字符串中是一个字节，wchar\_t\* 或 char16\_t\* 字符串中是两个字节，char32\_t\* 字符串中是四个字节。  
  
 字符串文本的最大长度为 65535 字节。 此限制适用于窄字符串文本和宽字符串文本。  
  
### 修改字符串文本  
 因为字符串（不包括 std:string 文本）是常量，所以尝试修改它们（例如，str\[2\] \= 'A'）会导致编译器错误。  
  
 **Microsoft 专用**  
  
 在 Visual C\+\+ 中，你可以使用字符串文本将指针初始化，使指针成为非常数 `char` 或 `wchar_t`。 可以在 C99 代码中使用，但 C\+\+98 中已弃用，C\+\+11 中已删除。 尝试修改该字符串将导致访问冲突，例如：  
  
```cpp  
wchar_t* str = L"hello"; str[2] = L'a'; // run-time error: access violation  
```  
  
 当你设置 [\/Zc:strictStrings（禁用字符串文本类型转换）](../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) 编译器选项且字符串文本转化为非常数字符指针时，可导致编译器发生错误。 我们建议将其用于符合标准的可移植代码。 使用 `auto` 关键字声明经过字符串文本初始化的指针也是一个很好的做法，因为它可以解析为正确（常数）的类型。 例如，此代码示例捕捉到一次在编译时写入字符串文本的尝试：  
  
```cpp  
auto str = L"hello"; str[2] = L'a'; // C3892: you cannot assign to a variable that is const.  
```  
  
 在某些情况下，可以合并相同的字符串文本，节省可执行文件的空间。 字符串文本合并过程中，编译器将导致对特定字符串文本的所有引用都指向内存中的同一位置，而不是每次引用都指向一个单独的字符串文本实例。 若要启用字符串合并，请使用 [\/GF](../build/reference/gf-eliminate-duplicate-strings.md) 编译器选项。  
  
 **结束 Microsoft 专用**  
  
### 串联相邻字符串文本  
 相邻宽或窄字符串文本是串联的。 声明如下：  
  
```cpp  
char str[] = "12" "34";  
```  
  
 与此声明相同：  
  
```cpp  
char atr[] = "1234";  
```  
  
 也和此声明相同：  
  
```cpp  
char atr[] =  "12\ 34";  
```  
  
 使用嵌入式十六进制转义代码来指定字符串会导致意外的结果。 以下示例旨在创建包含 ASCII 5 字符、后跟字符 f、i、v 和 e 的字符串文本：  
  
```cpp  
"\x05five"  
```  
  
 实际结果是十六进制 5F，它是一个下划线 ASCII 代码，后跟字符 i、v 和 e。 若要 获得正确的结果，可以使用以下方法之一：  
  
```cpp  
"\005five"     // Use octal literal. "\x05" "five"  // Use string splicing.  
```  
  
 std::string 文本，因为它们是 std::string 类型，可以与为 [basic\_string](../standard-library/basic-string-class.md) 类型定义的运算符 \+ 串联。 它们还可以通过与相邻字符串相同的方式进行串联。 在两种情况下，字符串编码和后缀都必须匹配：  
  
```cpp  
auto x1 = "hello" " " " world"; // OK auto x2 = U"hello" " " L"world"; // C2308: disagree on prefix auto x3 = u8"hello" " "s u8"world"s; // OK, agree on prefixes and suffixes auto x4 = u8"hello" " "s u8"world"z; // C3688, disagree on suffixes  
```  
  
### 具有通用字符名称的字符串文本  
 本机（非原始）字符串文本可能使用通用字符名称来表示任何字符，只要通用字符名称可被编码为字符串类型中的一个或多个字符。  例如，表示扩展字符的通用字符名称不能以使用 ANSI 代码页的窄字符串进行编码，但可以使用一些多字节代码页中的窄字符串、UTF\-8 字符串或宽字符串进行编码。 在 C\+\+11 中，通用字符名称支持由 char16\_t\* 和 char32\_t\* 字符串类型扩展：  
  
```cpp  
// ASCII smiling face const char*     s1 = ":-)"; // UTF-16 (on Windows) encoded WINKING FACE (U+1F609) const wchar_t*  s2 = L"😉 = \U0001F609 is ;-)"; // UTF-8  encoded SMILING FACE WITH HALO (U+1F607) const char*     s3 = u8"😇 = \U0001F607 is O:-)"; // UTF-16 encoded SMILING FACE WITH OPEN MOUTH (U+1F603) const char16_t* s4 = u"😃 = \U0001F603 is :-D"; // UTF-32 encoded SMILING FACE WITH SUNGLASSES (U+1F60E) const char32_t* s5 = U"😎 = \U0001F60E is B-)";  
```  
  
## 请参阅  
 [字符集](../cpp/character-sets2.md)   
 [数值、布尔和指针文本](../cpp/numeric-boolean-and-pointer-literals-cpp.md)   
 [用户定义的文本](../cpp/user-defined-literals-cpp.md)