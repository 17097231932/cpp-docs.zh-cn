---
title: basic_string_view 类
description: 的 API 引用， `basic_string_view` 它引用类似于字符的对象的恒定连续序列。
ms.date: 9/8/2020
f1_keywords:
- xstring/std::basic_string_view
- xstring/std::basic_string_view::allocator_type
- xstring/std::basic_string_view::const_iterator
- xstring/std::basic_string_view::const_pointer
- xstring/std::basic_string_view::const_reference
- xstring/std::basic_string_view::const_reverse_iterator
- xstring/std::basic_string_view::difference_type
- xstring/std::basic_string_view::ends_with
- xstring/std::basic_string_view::starts_with
- xstring/std::basic_string_view::iterator
- xstring/std::basic_string_view::npos
- xstring/std::basic_string_view::pointer
- xstring/std::basic_string_view::reference
- xstring/std::basic_string_view::reverse_iterator
- xstring/std::basic_string_view::size_type
- xstring/std::basic_string_view::traits_type
- xstring/std::basic_string_view::value_type
- xstring/std::basic_string_view::append
- xstring/std::basic_string_view::assign
- xstring/std::basic_string_view::at
- xstring/std::basic_string_view::back
- xstring/std::basic_string_view::begin
- xstring/std::basic_string_view::c_str
- xstring/std::basic_string_view::capacity
- xstring/std::basic_string_view::cbegin
- xstring/std::basic_string_view::cend
- xstring/std::basic_string_view::clear
- xstring/std::basic_string_view::compare
- xstring/std::basic_string_view::copy
- xstring/std::basic_string_view::_Copy_s
- xstring/std::basic_string_view::crbegin
- xstring/std::basic_string_view::crend
- xstring/std::basic_string_view::data
- xstring/std::basic_string_view::empty
- xstring/std::basic_string_view::end
- xstring/std::basic_string_view::erase
- xstring/std::basic_string_view::find
- xstring/std::basic_string_view::find_first_not_of
- xstring/std::basic_string_view::find_first_of
- xstring/std::basic_string_view::find_last_not_of
- xstring/std::basic_string_view::find_last_of
- xstring/std::basic_string_view::front
- xstring/std::basic_string_view::get_allocator
- xstring/std::basic_string_view::insert
- xstring/std::basic_string_view::length
- xstring/std::basic_string_view::max_size
- xstring/std::basic_string_view::pop_back
- xstring/std::basic_string_view::push_back
- xstring/std::basic_string_view::rbegin
- xstring/std::basic_string_view::rend
- xstring/std::basic_string_view::remove_prefix
- xstring/std::basic_string_view::remove_suffix
- xstring/std::basic_string_view::replace
- xstring/std::basic_string_view::reserve
- xstring/std::basic_string_view::resize
- xstring/std::basic_string_view::rfind
- xstring/std::basic_string_view::shrink_to_fit
- xstring/std::basic_string_view::size
- xstring/std::basic_string_view::substr
- xstring/std::basic_string_view::swap
helpviewer_keywords:
- std::basic_string_view
- std::basic_string_view, allocator_type
- std::basic_string_view, const_iterator
- std::basic_string_view, const_pointer
- std::basic_string_view, const_reference
- std::basic_string_view, const_reverse_iterator
- std::basic_string_view, difference_type
- std::basic_string_view, iterator
- std::basic_string_view, npos
- std::basic_string_view, pointer
- std::basic_string_view, reference
- std::basic_string_view, reverse_iterator
- std::basic_string_view, size_type
- std::basic_string_view, traits_type
- std::basic_string_view, value_type
- std::basic_string_view, append
- std::basic_string_view, assign
- std::basic_string_view, at
- std::basic_string_view, back
- std::basic_string_view, begin
- std::basic_string_view, c_str
- std::basic_string_view, capacity
- std::basic_string_view, cbegin
- std::basic_string_view, cend
- std::basic_string_view, clear
- std::basic_string_view, compare
- std::basic_string_view, copy
- std::basic_string_view, crbegin
- std::basic_string_view, crend
- std::basic_string_view, data
- std::basic_string_view, empty
- std::basic_string_view, end
- std::basic_string_view, ends_with
- std::basic_string_view, erase
- std::basic_string_view, find
- std::basic_string_view, find_first_not_of
- std::basic_string_view, find_first_of
- std::basic_string_view, find_last_not_of
- std::basic_string_view, find_last_of
- std::basic_string_view, front
- std::basic_string_view, get_allocator
- std::basic_string_view, insert
- std::basic_string_view, length
- std::basic_string_view, max_size
- std::basic_string_view, pop_back
- std::basic_string_view, push_back
- std::basic_string_view, rbegin
- std::basic_string_view, rend
- std::basic_string_view, remove_prefix
- std::basic_string_view, remove_suffix
- std::basic_string_view, replace
- std::basic_string_view, reserve
- std::basic_string_view, resize
- std::basic_string_view, rfind
- std::basic_string_view, shrink_to_fit
- std::basic_string_view, size
- std::basic_string_view, starts_with
- std::basic_string_view, substr
- std::basic_string_view, swap
ms.assetid: a9c3e0a2-39bf-4c8a-b093-9abe30839591
ms.openlocfilehash: 8eddf4bc6aae0338dc2e914aa57e6c1e7cc5c912
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040205"
---
# <a name="basic_string_view-class"></a>basic_string_view 类

类模板 `basic_string_view<charT>` 已添加到 c + + 17 中，以便函数接受各种不相关的字符串类型，而不需要在这些类型上模板化函数。 类将非拥有指针保存到连续的字符数据序列中，并指定一个长度来指定序列中的字符数。 对于序列是否以 null 结尾的情况，不进行任何假设。

标准库根据元素类型定义几个专用化：

- `string_view`
- `wstring_view`
- `u16string_view`
- `u32string_view`

在本文档中，术语 "string_view" 通常指的是这些 typedef 中的任何一个。

String_view 描述读取字符串数据所需的最低公共接口。 它提供对基础数据的 const 访问;除了函数) 以外，它不 (任何副本 `copy` 。 数据在任何位置都不能包含 null 值 ( "\ 0" ) 。 String_view 无法控制对象的生存期。 调用方负责确保基础字符串数据有效。

接受 string_view 类型的参数的函数可用于任何类似于字符串的类型，而不会使函数进入模板，也不会将函数约束到字符串类型的特定子集。 唯一的要求是存在从字符串类型到 string_view 的隐式转换。 所有标准字符串类型都可隐式转换为包含相同元素类型的 string_view。 换言之， `std::string` 可以转换为，但不能转换为 `string_view` `wstring_view` 。

下面的示例演示一个采用类型为的参数的非模板函数 `f` `wstring_view` 。 可以通过类型为、和的参数调用它 `std::wstring` `wchar_t*` `winrt::hstring` 。

```cpp
// compile with: /std:c++17
// string_view that uses elements of wchar_t
void f(wstring_view);

// pass a std::wstring:
const std::wstring& s { L"Hello" };
f(s);

// pass a C-style null-terminated string (string_view is not null-terminated):
const wchar_t* ns = L"Hello";
f(ns);

// pass a C-style character array of len characters (excluding null terminator):
const wchar_t* cs { L"Hello" };
size_t len { 5 };
f({cs,len});

// pass a WinRT string
winrt::hstring hs { L"Hello" };
f(hs);
```

## <a name="syntax"></a>语法

```cpp
template <class CharType, class Traits = char_traits<CharType>>
class basic_string_view;
```

### <a name="parameters"></a>参数

*CharType*\
存储在 string_view 中的字符的类型。 C + + 标准库为此模板的专用化提供以下 typedef。

- 类型的元素的[string_view](../standard-library/string-view-typedefs.md#string_view)**`char`**
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view)，用于 **`wchar_t`**
- [u16string_view](../standard-library/string-view-typedefs.md#u16string_view)**`char16_t`**
- [u32string_view](../standard-library/string-view-typedefs.md#u32string_view) **`char32_t`** 。

*特征*\
默认为[char_traits](char-traits-struct.md) < *CharType*>。

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[basic_string_view](#basic_string_view)|构造一个空的 string_view，或指向某个其他字符串对象数据的全部或部分，或指向 C 样式字符数组的。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|**const_iterator**|可读取元素的随机访问迭代器 **`const`** 。|
|**const_pointer**|`using const_pointer = const value_type*;`|
|**const_reference**|`using const_reference = const value_type&;`|
|**const_reverse_iterator**|`using const_reverse_iterator = std::reverse_iterator<const_iterator>;`|
|**difference_type**|`using difference_type = ptrdiff_t;`|
|**器**|`using iterator = const_iterator;`|
|**npos**|`static constexpr size_type npos = size_type(-1);`|
|**变为**|`using pointer = value_type*;`|
|**reference**|`using reference = value_type&;`|
|**reverse_iterator**|`using reverse_iterator = const_reverse_iterator;`|
|**size_type**|`using size_type = size_t;`|
|**traits_type**|`using traits_type = Traits;`|
|**value_type**|`using value_type = CharType;`|

### <a name="member-operators"></a>成员运算符

|运算符|说明|
|-|-|
|[operator =](#op_eq)|将 string_view 或可转换的字符串对象分配给另一个 string_view。|
|[操作员\[\]](#op_at)|返回指定索引处的元素。|

### <a name="member-functions"></a>成员函数

|成员函数|说明|
|-|-|
|[at](#at)|返回 const_reference 到指定位置的元素。|
|[返回](#back)|返回最后一个元素的 const_reference。|
|[准备](#begin)|返回寻址第一个元素的常量迭代器。  (string_views 是不可变的。 ) |
|[cbegin](#cbegin)|与 [begin](#begin)相同。|
|[cend](#cend)|返回一个常量迭代器，该迭代器指向最后一个元素之后的一个。|
|[copy](#copy)|从源 string_view 中的索引位置到目标字符数组，最多复制指定数目的字符。 不建议 (。 改用 _Copy_s。 ) |
|[_Copy_s](#_copy_s)|安全 CRT 复制函数。|
|[并排](#compare)|将 string_view 与指定的 string_view 进行比较，以确定它们是否相等，或者按字典顺序是否小于另一个。|
|[crbegin](#crbegin)|与 [rbegin](#rbegin)相同。|
|[crend](#crend)|与 [rend](#rend)相同。|
|[data](#data)|返回指向字符序列的原始非所有者指针。|
|[empty](#empty)|测试 string_view 是否包含字符。|
|[end](#end)|与 [cend](#cend)相同。|
|[ends_with](#ends_with)<sup>c + + 20</sup>|检查字符串视图是否以指定的后缀结尾。|
|[find](#find)|向前搜索与指定字符序列匹配的子字符串的第一个匹配项。|
|[find_first_not_of](#find_first_not_of)|搜索不属于指定 string_view 或可转换的字符串对象的任何元素的第一个字符。|
|[find_first_of](#find_first_of)|搜索与指定 string_view 或可转换的字符串对象的任何元素匹配的第一个字符。|
|[find_last_not_of](#find_last_not_of)|搜索不属于指定 string_view 或可转换字符串对象的任何元素的最后一个字符。|
|[find_last_of](#find_last_of)|搜索作为指定 string_view 或可转换的字符串对象的元素的最后一个字符。|
|[主](#front)|返回第一个元素的 const_reference。|
|[length](#length)|返回元素的当前数目。|
|[max_size](#max_size)|返回 string_view 可包含的最大字符数。|
|[rbegin](#rbegin)|返回一个常量迭代器，该迭代器用于发现反向 string_view 中的第一个元素。|
|[remove_prefix](#remove_prefix)|将指针向后移动指定数量的元素。|
|[remove_suffix](#remove_suffix)|从后面开始，将视图的大小减少到指定数目的元素。|
|[rend](#rend)|返回一个常量迭代器，该迭代器指向反向 string_view 中最后一个元素之后的一个。|
|[rfind](#rfind)|反向搜索 string_view 与指定字符序列匹配的第一个子字符串。|
|[大小](#size)|返回元素的当前数目。|
|[starts_with](#starts_with)<sup>c + + 20</sup>|检查字符串视图是否以给定的前缀开头。|
|[substr](#substr)|返回从指定索引处开始的指定长度的子字符串。|
|[swap](#swap)|交换两个 string_views 的内容。|

## <a name="remarks"></a>备注

如果要求函数生成的序列长于 [max_size](#max_size) 元素，这个函数将通过引发 [length_error](../standard-library/length-error-class.md) 类型的对象来报告长度错误。

## <a name="requirements"></a>要求

[std： c + + 17](../build/reference/std-specify-language-standard-version.md) 或更高版本。

**标头：**\<string_view>

**命名空间:** std

## <a name="basic_string_viewat"></a><a name="at"></a> basic_string_view：： at

返回一个 const_reference，该字符串指向指定的从零开始的索引处的字符。

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>参数

*抵销*\
要引用的元素的索引。

### <a name="return-value"></a>返回值

Const_reference 到参数索引所指定位置处的字符。

### <a name="remarks"></a>备注

第一个元素的索引为零，后面的元素按正整数连续索引，以便长度为*n*的 string_view 包含第 n 个索引*的第 n**个*元素。 与[ \[ 运算符 \] ](#op_at)不同，**中**的无效索引会引发异常。

一般情况下，我们建议 **在** 中对诸如和之类的序列 `std::vector` 使用 string_view。 传递给序列的无效索引是一个逻辑错误，应在开发过程中发现并修复该错误。 如果程序并不确定其索引是否有效，应对其进行测试，而不是调用 ( # A1，并依赖于异常来防御粗心编程。

有关详细信息，请参阅[basic_string_view：： operator \[ \] ](#op_at) 。

### <a name="example"></a>示例

```cpp
// basic_string_view_at.cpp
// compile with: /EHsc
#include <string_view>
#include <iostream>

int main()
{
    using namespace std;

    const string_view  str1("Hello world");
    string_view::const_reference refStr2 = str1.at(8); // 'r'
}
```

## <a name="basic_string_viewback"></a><a name="back"></a> basic_string_view：： back

返回最后一个元素的 const_reference。

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>返回值

Const_reference 到 string_view 中的最后一个元素。

### <a name="remarks"></a>备注

如果 string_view 为空，则引发异常。

请记住，在修改 string_view （例如通过调用）后， `remove_suffix` 此函数返回的元素不再是基础数据中的最后一个元素。

### <a name="example"></a>示例

`string_view`用 C 字符串文本构造的不包括终止 null。 因此，在下面的示例中，将 `back` 返回 `'p'` 而不是 `'\0'` 。

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p
```

嵌入的 null 值被视为任何其他字符：

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_viewbasic_string_view"></a><a name="basic_string_view"></a> basic_string_view：： basic_string_view

构造 string_view。

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>参数

*字符串*\
指向字符值的指针。

*长度*\
要在视图中包含的字符数。

### <a name="remarks"></a>备注

带有 charT * 参数的构造函数假设输入以 null 值终止，但是终止 null 未包含在 string_view 中。

你还可以使用文本构造 string_view。 请参阅 [运算符 "" sv](string-view-operators.md#op_sv)。

## <a name="basic_string_viewbegin"></a><a name="begin"></a> basic_string_view：： begin

与 [cbegin](#cbegin)相同。

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>返回值

返回寻址第一个元素 const_iterator。

## <a name="basic_string_viewcbegin"></a><a name="cbegin"></a> basic_string_view：： cbegin

返回一个用于寻址范围中第一个元素的 const_iterator。

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>返回值

一个 **`const`** 随机访问迭代器，指向范围的第一个元素，或刚超出空范围末尾 (空范围) 的位置 `cbegin() == cend()` 。

## <a name="basic_string_viewcend"></a><a name="cend"></a> basic_string_view：： cend

返回一个 const_iterator，该用于寻址范围内最后一个元素之外的位置。

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>返回值

一个 **`const`** 随机访问迭代器，它指向刚超出范围末尾的位置。

### <a name="remarks"></a>备注

返回的值 `cend` 不应被取消引用。

## <a name="basic_string_viewcompare"></a><a name="compare"></a> basic_string_view：： compare

与指定 string_view (或可转换的字符串类型进行区分大小写的比较) ，以确定两个对象是否相等，或按字典顺序是否小于另一个。 [ \<string_view> 运算符](string-view-operators.md)使用此成员函数进行比较。

```cpp
constexpr int compare(basic_string_view strv) const noexcept;
constexpr int compare(size_type pos, size_type num, basic_string_view strv) const;
constexpr int compare(size_type pos, size_type num, basic_string_view strv, size_type offset, size_type num2) const;
constexpr int compare(const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr, size_type num2) const;
```

### <a name="parameters"></a>参数

*strv*\
要与此 string_view 进行比较的 string_view。

*位置*\
此 string_view 的索引，比较从此位置开始比较。

*编号*\
此 string_view 要比较的最大字符数。

*num2*\
要比较的 *strv* 中的最大字符数。

*抵销*\
开始比较的 *strv* 的索引。

*ptr*\
要与此 string_view 进行比较的 C 字符串。

### <a name="return-value"></a>返回值

- 如果此值 `string_view` 小于*strv*或*ptr* ，则为负值
- 如果两个字符序列相等，则为零
- 如果此值 `string_view` 大于*strv*或*ptr* ，则为正值

### <a name="remarks"></a>备注

`compare`成员函数对每个字符序列的全部或部分执行区分大小写的比较。

### <a name="example"></a>示例

```cpp
// basic_string_view_compare.cpp
// compile with: /EHsc
#include <string_view>
#include <iostream>
#include <string>

using namespace std;

string to_alpha(int result)
{
   if (result < 0) return " less than ";
   else if (result == 0) return " equal to ";
   else return " greater than ";
}

int main()
{
   // The first member function compares
   // two string_views
   string_view sv_A("CAB");
   string_view sv_B("CAB");
   cout << "sv_A is " << sv_A << endl;
   cout << "sv_B is " << sv_B << endl;
   int comp1 = sv_A.compare(sv_B);
   cout << "sv_A is" << to_alpha(comp1) << "sv_B.\n";

   // The second member function compares part of
   // an operand string_view to another string_view
   string_view sv_C("AACAB");
   string_view sv_D("CAB");
   cout << "sv_C is: " << sv_C << endl;
   cout << "sv_D is: " << sv_D << endl;
   int comp2a = sv_C.compare(2, 3, sv_D);
   cout << "The last three characters of sv_C are"
       << to_alpha(comp2a) << "sv_D.\n";

   int comp2b = sv_C.compare(0, 3, sv_D);
   cout << "The first three characters of sv_C are"
       << to_alpha(comp2b) << "sv_D.\n";

   // The third member function compares part of
   // an operand string_view to part of another string_view
   string_view sv_E("AACAB");
   string_view sv_F("DCABD");
   cout << "sv_E: " << sv_E << endl;
   cout << "sv_F is: " << sv_F << endl;
   int comp3a = sv_E.compare(2, 3, sv_F, 1, 3);
   cout << "The three characters from position 2 of sv_E are"
       << to_alpha(comp3a)
       << "the 3 characters of sv_F from position 1.\n";

   // The fourth member function compares
   // an operand string_view to a C string
   string_view sv_G("ABC");
   const char* cs_A = "DEF";
   cout << "sv_G is: " << sv_G << endl;
   cout << "cs_A is: " << cs_A << endl;
   int comp4a = sv_G.compare(cs_A);
   cout << "sv_G is" << to_alpha(comp4a) << "cs_A.\n";

   // The fifth member function compares part of
   // an operand string_view to a C string
   string_view sv_H("AACAB");
   const char* cs_B = "CAB";
   cout << "sv_H is: " << sv_H << endl;
   cout << "cs_B is: " << cs_B << endl;
   int comp5a = sv_H.compare(2, 3, cs_B);
   cout << "The last three characters of sv_H are"
      << to_alpha(comp5a) << "cs_B.\n";

   // The sixth member function compares part of
   // an operand string_view to part of an equal length of
   // a C string
   string_view sv_I("AACAB");
   const char* cs_C = "ACAB";
   cout << "sv_I is: " << sv_I << endl;
   cout << "cs_C: " << cs_C << endl;
   int comp6a = sv_I.compare(1, 3, cs_C, 3);
   cout << "The 3 characters from position 1 of sv_I are"
      << to_alpha(comp6a) << "the first 3 characters of cs_C.\n";
}
```

```Output
sv_A is CAB
sv_B is CAB
sv_A is equal to sv_B.
sv_C is: AACAB
sv_D is: CAB
The last three characters of sv_C are equal to sv_D.
The first three characters of sv_C are less than sv_D.
sv_E: AACAB
sv_F is: DCABD
The three characters from position 2 of sv_E are equal to the 3 characters of sv_F from position 1.
sv_G is: ABC
cs_A is: DEF
sv_G is less than cs_A.
sv_H is: AACAB
cs_B is: CAB
The last three characters of sv_H are equal to cs_B.
sv_I is: AACAB
cs_C: ACAB
The 3 characters from position 1 of sv_I are equal to the first 3 characters of cs_C.
```

## <a name="basic_string_viewcopy"></a><a name="copy"></a> basic_string_view：： copy

从源 string_view 中的索引位置到目标字符数组，最多复制指定数目的字符。 建议改用安全函数 [basic_string_view：： _Copy_s](#_copy_s) 。

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>参数

*ptr*\
要复制的元素的目标字符数组。

*计*\
最多从源 string_view 复制的字符数。

*抵销*\
要从中进行复制的源 string_view 中的开始位置。

### <a name="return-value"></a>返回值

复制的字符数。

### <a name="remarks"></a>备注

空字符不追加到副本的末尾。

## <a name="basic_string_view_copy_s"></a><a name="_copy_s"></a> basic_string_view：： _Copy_s

要使用的安全 CRT 复制函数（而不是 [复制](#copy)）。

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>参数

*目的*\
要复制的元素的目标字符数组。

*dest_size*\
*Dest*的大小。

_ *计算* 要从源字符串复制的最多字符数。

*_Off*\
要进行复制的源字符串中的开始位置。

### <a name="return-value"></a>返回值

复制的字符数。

### <a name="remarks"></a>备注

空字符不追加到副本的末尾。

有关详细信息，请参阅- [crt 中的 c 运行时库/安全功能](../c-runtime-library/security-features-in-the-crt.md)。

## <a name="basic_string_viewcrbegin"></a><a name="crbegin"></a> basic_string_view：： crbegin

返回一个 const_reverse_iterator，该用于寻址反向 string_view 中的第一个元素。

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>返回值

用于寻址反向 string_view 中第一个元素的 const_reverse_iterator。

## <a name="basic_string_viewcrend"></a><a name="crend"></a> basic_string_view：： crend

与 [rend](#rend)相同。

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>返回值

返回一个 const_reverse_iterator，用于解决反向 string_view 结束后的一个。

## <a name="basic_string_viewdata"></a><a name="data"></a> basic_string_view：:d ata

返回一个原始非拥有指针，该指针指向用于构造 string_view 的对象的 const 字符序列。

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>返回值

指向字符序列中第一个元素的指向常量的指针。

### <a name="remarks"></a>备注

指针无法修改字符。

String_view 字符的序列不一定以 null 结尾。 的返回类型 `data` 不是有效的 C 字符串，因为不追加 null 字符。 空字符 "\ 0" 在类型 string_view 的对象中没有任何特殊含义，可能与任何其他字符一样是 string_view 对象的一部分。

## <a name="basic_string_viewempty"></a><a name="empty"></a> basic_string_view：： empty

测试 string_view 是否包含字符。

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>返回值

**`true`** 如果 string_view 对象不包含任何字符，则为; 否则为。 **`false`** 如果至少有一个字符。

### <a name="remarks"></a>备注

成员函数等效于 [size](#size) ( # A1 = = 0。

## <a name="basic_string_viewend"></a><a name="end"></a> basic_string_view：： end

返回指向最后一个元素之后的一个随机访问 const_iterator。

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>返回值

返回指向最后一个元素之后的一个随机访问 const_iterator。

### <a name="remarks"></a>备注

`end` 用于测试 const_iterator 是否已到达其 string_view 的结尾。 返回的值 `end` 不应被取消引用。

## <a name="basic_string_viewends_with"></a><a name="ends_with"></a> basic_string_view：： ends_with

检查字符串视图是否以指定的后缀结尾。

```cpp
bool ends_with(const CharType c) const noexcept;
bool ends_with(const CharType* const x) const noexcept;
bool ends_with(const basic_string_view sv) const noexcept;
```

### <a name="parameters"></a>参数

*ansi-c*\
要查找的单字符后缀。

*sv*\
包含要查找的后缀的字符串视图。
可以传递 `std::basic_string` 转换为字符串视图的。

*x-blade*\
以 Null 结尾的字符串，其中包含要查找的后缀。

### <a name="return-value"></a>返回值

`true` 如果字符串视图以指定的后缀结尾，则为; 否则为。 `false` 否则为。

### <a name="remarks"></a>备注

`ends_with()` 是 c + + 20 中的新增项。 若要使用它，请指定 [/std： c + + 最新](../build/reference/std-specify-language-standard-version.md) 编译器选项。

请参阅 [starts_with](#starts_with) 以检查字符串视图是否以指定的前缀开头。

### <a name="example"></a>示例

```cpp
// Requires /std:c++latest
#include <string>
#include <iostream>

int main()
{
    std::cout << std::boolalpha; // so booleans show as 'true'/'false'  
    std::cout << std::string_view("abcdefg").ends_with('g') << '\n';
    std::cout << std::string_view("abcdefg").ends_with("eFg") << '\n';

    std::basic_string<char> str2 = "efg";
    std::cout << std::string_view("abcdefg").ends_with(str2);

    return 0;
}
```

```Output
true
false
true
```

## <a name="basic_string_viewfind"></a><a name="find"></a> basic_string_view：： find

向前搜索某个 `string_view` 字符或子字符串的第一个匹配项，查找与指定字符序列 () 的第一个匹配项。

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>参数

*字符串*\
`string_view`成员函数要搜索的。

*chVal*\
成员函数要搜索的字符值。

*抵销*\
要开始搜索的索引。

*ptr*\
要搜索其成员函数的 C 字符串。

*计*\
*Ptr*中从第一个字符开始计数的字符数。

### <a name="return-value"></a>返回值

搜索成功时，则为搜索的子字符串的首个字符的索引；否则为 `npos`。

## <a name="basic_string_viewfind_first_not_of"></a><a name="find_first_not_of"></a> basic_string_view：： find_first_not_of

搜索不属于指定 string_view 或可转换的字符串对象的元素的第一个字符。

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>参数

*字符串*\
成员函数要搜索的 string_view。

*chVal*\
成员函数要搜索的字符值。

*抵销*\
要开始搜索的索引。

*ptr*\
要搜索其成员函数的 C 字符串。

*计*\
成员函数要搜索的 C 字符串中从第一个字符开始计数的字符数。

### <a name="return-value"></a>返回值

搜索成功时，则为搜索的子字符串的首个字符的索引；否则为 `npos`。

## <a name="basic_string_viewfind_first_of"></a><a name="find_first_of"></a> basic_string_view：： find_first_of

搜索与指定 string_view 的任何元素匹配的第一个字符。

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>参数

*chVal*\
成员函数要搜索的字符值。

*抵销*\
要开始搜索的索引。

*ptr*\
要搜索其成员函数的 C 字符串。

*计*\
成员函数要搜索的 C 字符串中从第一个字符开始计数的字符数。

*字符串*\
成员函数要搜索的 string_view。

### <a name="return-value"></a>返回值

搜索成功时，则为搜索的子字符串的首个字符的索引；否则为 `npos`。

## <a name="basic_string_viewfind_last_not_of"></a><a name="find_last_not_of"></a> basic_string_view：： find_last_not_of

搜索不属于指定 string_view 的任何元素的最后一个字符。

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>参数

*字符串*\
成员函数要搜索的 string_view。

*chVal*\
成员函数要搜索的字符值。

*抵销*\
要完成搜索的索引。

*ptr*\
要搜索其成员函数的 C 字符串。

*计*\
*Ptr*中从第一个字符开始计数的字符数。

### <a name="return-value"></a>返回值

搜索成功时，则为搜索的子字符串的首个字符的索引；否则为 `string_view::npos`。

## <a name="basic_string_viewfind_last_of"></a><a name="find_last_of"></a> basic_string_view：： find_last_of

搜索与指定 string_view 的任何元素匹配的最后一个字符。

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>参数

*字符串*\
成员函数要搜索的 string_view。

*chVal*\
成员函数要搜索的字符值。

*抵销*\
要完成搜索的索引。

*ptr*\
要搜索其成员函数的 C 字符串。

*计*\
成员函数要搜索的 C 字符串中从第一个字符开始计数的字符数。

### <a name="return-value"></a>返回值

搜索成功时，则为搜索的子字符串的最后一个字符的索引；否则为 `npos`。

## <a name="basic_string_viewfront"></a><a name="front"></a> basic_string_view：：前门

返回第一个元素的 const_reference。

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>返回值

第一个元素的 const_reference。

### <a name="remarks"></a>备注

如果 string_view 为空，则引发异常。

## <a name="basic_string_viewlength"></a><a name="length"></a> basic_string_view：： length

返回元素的当前数目。

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>备注

成员函数与 [size](#size) 相同。

## <a name="basic_string_viewmax_size"></a><a name="max_size"></a> basic_string_view：： max_size

返回 string_view 可包含的最大字符数。

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>返回值

String_view 可包含的最大字符数。

### <a name="remarks"></a>备注

当操作生成的 string_view 的长度大于时，将引发 [length_error](../standard-library/length-error-class.md) 类型的异常 `max_size()` 。

## <a name="basic_string_viewoperator"></a><a name="op_eq"></a> basic_string_view：： operator =

将 string_view 或可转换的字符串对象分配给另一个 string_view。

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```

### <a name="example"></a>示例

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```

## <a name="basic_string_viewoperator"></a><a name="op_at"></a> basic_string_view：： operator []

向具有指定索引的字符提供 const_reference。

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>参数

*抵销*\
要引用的元素的索引。

### <a name="return-value"></a>返回值

Const_reference 到参数索引所指定位置处的字符。

### <a name="remarks"></a>备注

第一个元素的索引为零，后面的元素按正整数连续索引，使长度为*n*的 string_view 具有*第 n 个索引的第 n**个元素*。

`operator[]` 比的 [成员函数快，用于](#at) 提供对 string_view 的元素的读取访问权限。

`operator[]` 不检查作为参数传递的索引是否有效。 传递给的无效索引 `operator[]` 导致未定义的行为。

如果基础字符串数据由所属对象修改或删除，则返回的引用可能会无效。

当使用[ \_ 迭代器 \_ 调试 \_ 级别](../standard-library/iterator-debug-level.md)设置为1或2进行编译时，如果尝试访问位于 string_view 边界之外的元素，将发生运行时错误。 有关更多信息，请参见 [Checked Iterators](../standard-library/checked-iterators.md)。

## <a name="basic_string_viewrbegin"></a><a name="rbegin"></a> basic_string_view：： rbegin

返回反向 string_view 中第一个元素的常量迭代器。

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>返回值

返回反向 string_view 中第一个元素的随机访问迭代器，该迭代器将成为相应非反向 string_view 中的最后一个元素。

### <a name="remarks"></a>备注

`rbegin` 与反向 string_view 一起使用，正如 [begin](#begin) 用于 string_view。 `rbegin` 可用于向后重初始化迭代。

## <a name="basic_string_viewremove_prefix"></a><a name="remove_prefix"></a> basic_string_view：： remove_prefix

将指针向后移动指定数量的元素。

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>备注

使基础数据保持不变。 将 string_view 指针向前移动 n 个元素，并将私有 `size` 数据成员设置为大小-n。

## <a name="basic_string_viewremove_suffix"></a><a name="remove_suffix"></a> basic_string_view：： remove_suffix

从后面开始，将视图的大小减少到指定数目的元素。

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>备注

使基础数据保持不变。 将私有 `size` 数据成员设置为大小-n。

## <a name="basic_string_viewrend"></a><a name="rend"></a> basic_string_view：： rend

返回一个常量迭代器，该迭代器指向反向 string_view 中最后一个元素之后的一个。

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>返回值

一个常量反向随机访问迭代器，它指向反向 string_view 中最后一个元素之后的一个。

### <a name="remarks"></a>备注

`rend` 与反向 string_view 一起使用，正如 [end](#end) 与 string_view 一起使用一样。 `rend` 可用于测试反向迭代器是否已到达其 string_view 的末尾。 返回的值 `rend` 不应被取消引用。

## <a name="basic_string_viewrfind"></a><a name="rfind"></a> basic_string_view：： rfind

反向搜索与指定字符序列匹配的子字符串的 string_view。

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>参数

*chVal*\
成员函数要搜索的字符值。

*抵销*\
要开始搜索的索引。

*ptr*\
要搜索其成员函数的 C 字符串。

*计*\
成员函数要搜索的 C 字符串中从第一个字符开始计数的字符数。

*字符串*\
成员函数要搜索的 string_view。

### <a name="return-value"></a>返回值

成功时子字符串的第一个字符的索引;否则为 `npos` 。

## <a name="basic_string_viewsize"></a><a name="size"></a> basic_string_view：： size

返回 string_view 中的元素数。

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>返回值

String_view 的长度。

### <a name="remarks"></a>备注

String_view 可以修改其长度，例如 `remove_prefix` 和 `remove_suffix` 。 因为这不会修改基础字符串数据，所以 string_view 的大小不一定是基础数据的大小。

## <a name="basic_string_viewstarts_with"></a><a name="starts_with"></a> basic_string_view：： starts_with

检查字符串视图是否以指定的前缀开头。

```cpp
bool starts_with(const CharType c) const noexcept;
bool starts_with(const CharType* const x) const noexcept;
bool starts_with(const basic_string_view sv) const noexcept;
```

### <a name="parameters"></a>参数

*ansi-c*\
要查找的单字符前缀。

*sv*\
一个包含要查找的前缀的字符串视图。
可以传递 `std::basic_string` 转换为字符串视图的。

*x-blade*\
以 Null 结尾的字符串，其中包含要查找的前缀。

### <a name="return-value"></a>返回值

`true` 如果字符串以指定的前缀开头，则为; 否则为。 `false` 否则为。

### <a name="remarks"></a>备注

`starts_with()` 是 c + + 20 中的新增项。 若要使用它，请指定 [/std： c + + 最新](../build/reference/std-specify-language-standard-version.md) 编译器选项。

请参阅 [ends_with](#ends_with) ，查看字符串是否以后缀结尾。

### <a name="example"></a>示例

```cpp
// Requires /std:c++latest
#include <string>
#include <iostream>

int main()
{
    std::cout << std::boolalpha; // so booleans show as 'true'/'false'  
    std::cout << std::string_view("abcdefg").starts_with('b') << '\n';
    std::cout << std::string_view("abcdefg").starts_with("aBc") << '\n';

    std::basic_string<char> str2 = "abc";
    std::cout << std::string_view("abcdefg").starts_with(str2);

    return 0;
}
```

```Output
false
false
true
```

## <a name="basic_string_viewsubstr"></a><a name="substr"></a> basic_string_view：： substr

返回一个 string_view，它最多 (指定位置) 指定数目的字符。

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>参数

*抵销*\
在从其进行复制的位置查找元素的索引，默认值为0。

*计*\
要包括在子字符串中的字符数（如果存在）。

### <a name="return-value"></a>返回值

一个 string_view 对象，该对象表示元素的指定子序列。

## <a name="basic_string_viewswap"></a><a name="swap"></a> basic_string_view：： swap

交换两个 string_views，换言之，指向基础字符串数据的指针和大小值。

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>参数

*sv*\
要与目标 string_view 的链接和大小值进行交换的源 string_view。

## <a name="see-also"></a>另请参阅

[\<string_view>](../standard-library/string-view.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
