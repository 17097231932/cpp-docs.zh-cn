---
title: '&lt;string_view &gt; 运算符'
ms.date: 04/19/2019
f1_keywords:
- xstring/basic_string_view::operator!=
- xstring/basic_string_view::operator&gt;
- xstring/basic_string_view::operator&gt;=
- xstring/basic_string_view::operator&lt;
- xstring/basic_string_view::operator&lt;&lt;
- xstring/basic_string_view::operator&lt;=
- xstring/basic_string_view::operator+
- xstring/basic_string_view::operator==
helpviewer_keywords:
- std::basic_string_view::operator!=
- std::basic_string_view::operator&gt;
- std::basic_string_view::operator&gt;=
- std::basic_string_view::operator&lt;
- std::basic_string_view::operator&lt;&lt;
- std::basic_string_view::operator&lt;=, std::basic_string_view::operator==
ms.openlocfilehash: b0761c1af7b2ed9f34917d2e4165561b357f0a30
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833213"
---
# <a name="ltstring_viewgt-operators"></a>&lt;string_view &gt; 运算符

使用这些运算符比较两个 string_view 对象，或 string_view 以及为其提供了隐式转换的其他某个字符串对象 (例如[std：： string](basic-string-class.md)或**char \* **) 。

[operator！ =](#op_neq)\
[操作员&gt;](#op_gt)\
[操作员&gt;=](#op_gt_eq)\
[操作员&lt;](#op_lt)\
[操作员&lt;&lt;](#op_lt_lt)\
[操作员&lt;=](#op_lt_eq)\
[operator = =](#op_eq_eq)\
[运算符 "" sv](#op_sv)

## <a name="operator"></a><a name="op_neq"></a> operator！ =

测试运算符左侧的对象是否不等于右侧的对象。

```cpp
template <class CharType, class Traits>
bool operator!=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator!=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator!=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>参数

*左中*\
任何可转换的字符串类型或要比较的类型的对象 `basic_string_view` 。

*然后*\
任何可转换的字符串类型或要比较的类型的对象 `basic_string_view` 。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的对象不按字典顺序等于右侧的对象，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>注解

从 *convertible_string_type* 到另一侧的 string_view 必须存在隐式转换。

比较基于对字符序列进行成对字典比较。 如果它们具有相同数量的元素，并且元素都相等，则这两个对象相等。 否则，它们不相等。

## <a name="operator"></a><a name="op_eq_eq"></a> operator = =

测试运算符左侧的对象是否等于右侧的对象。

```cpp
template <class CharType, class Traits>
bool operator==(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator==(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator==(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>参数

*左中*\
任何可转换的字符串类型或要比较的类型的对象 `basic_string_view` 。

*然后*\
任何可转换的字符串类型或要比较的类型的对象 `basic_string_view` 。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的对象按字典顺序等于右侧的对象，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>注解

从 *convertible_string_type* 到另一侧的 string_view 必须存在隐式转换。

比较基于对字符序列进行成对字典比较。 如果它们具有相同数量的元素，并且元素都相等，则这两个对象相等。

## <a name="operatorlt"></a><a name="op_lt"></a> 操作员&lt;

测试运算符左侧的对象是否小于右端的对象 sidestring_view

```cpp
template <class CharType, class Traits>
bool operator<(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator<(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator<(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>参数

*左中*\
任何可转换的字符串类型或要比较的类型的对象 `basic_string_view` 。

*然后*\
任何可转换的字符串类型或要比较的类型的对象 `basic_string_view` 。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的对象按字典顺序小于右侧的对象，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>注解

从 *convertible_string_type* 到另一侧的 string_view 必须存在隐式转换。

比较基于对字符序列进行成对字典比较。 当遇到第一对不相等的字符时，将返回该比较的结果。 如果未找到不相等的字符，但一个序列较短，则较短的序列小于较长的序列。 换句话说，"cat" 小于 "猫"。

### <a name="example"></a>示例

```cpp
#include <string>
#include <string_view>

using namespace std;

int main()
{
    string_view sv1 { "ABA" };
    string_view sv2{ "ABAC" };
    string_view sv3{ "ABAD" };
    string_view sv4{ "ABACE" };

    bool result = sv2 > sv1; // true
    result = sv3 > sv2; // true
    result = sv3 != sv1; // true
    result = sv4 < sv3; // true because `C` < `D`
}
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a> 操作员&lt;=

测试运算符左侧的对象是否小于或等于右侧的对象。

```cpp
template <class CharType, class Traits>
bool operator<=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator<=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator<=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>参数

*左中*\
任何可转换的字符串类型或要比较的类型的对象 `basic_string_view` 。

*然后*\
任何可转换的字符串类型或要比较的类型的对象 `basic_string_view` 。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的对象按字典顺序小于或等于右侧的对象，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>注解

请[参阅 &lt; 运算符](#op_lt)。

## <a name="operatorltlt"></a><a name="op_lt_lt"></a> 操作员&lt;&lt;

将 string_view 写入到输出流中。

```cpp
template <class CharType, class Traits>
inline basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& Ostr, const basic_string_view<CharType, Traits> Str);
```

### <a name="parameters"></a>参数

*Ostr*\
要写入的输出流。

*字符串*\
要输入到输出流中的 string_view。

### <a name="return-value"></a>返回值

要写入的输出流。

### <a name="remarks"></a>注解

使用此运算符将 string_view 的内容插入到输出流中，例如使用 [std：： cout](iostream.md#cout)。

## <a name="operatorgt"></a><a name="op_gt"></a> 操作员&gt;

测试运算符左侧的对象是否大于右侧的对象。

```cpp
template <class CharType, class Traits>
bool operator>(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator>(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator>(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>参数

*左中*\
任何可转换的字符串类型或要比较的类型的对象 `basic_string_view` 。

*然后*\
任何可转换的字符串类型或要比较的类型的对象 `basic_string_view` 。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的对象按字典顺序大于右侧的 string_view 对象，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>注解

请[参阅 &lt; 运算符](#op_lt)。

## <a name="operatorgt"></a><a name="op_gt_eq"></a> 操作员&gt;=

测试运算符左侧的对象是否大于或等于右侧的对象。

```cpp
template <class CharType, class Traits>
bool operator>=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator>=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator>=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>参数

*左中*\
任何可转换的字符串类型或要比较的类型的对象 `basic_string_view` 。

*然后*\
任何可转换的字符串类型或要比较的类型的对象 `basic_string_view` 。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的对象按字典顺序大于或等于右侧的对象，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>注解

请[参阅 &lt; 运算符](#op_lt)。

## <a name="operator-sv-string_view-literal"></a><a name="op_sv"></a> 运算符 "" sv (string_view 文本) 

从字符串文本构造 string_view。 需要命名空间 `std::literals::string_view_literals` 。

### <a name="example"></a>示例

```cpp

using namespace std;
using namespace literals::string_view_literals;

    string_view sv{ "Hello"sv };
    wstring_view wsv{ L"Hello"sv };
    u16string_view sv16{ u"Hello"sv };
    u32string_view sv32{ U"Hello"sv };
```

## <a name="see-also"></a>另请参阅

[\<string_view>](../standard-library/string-view.md)
