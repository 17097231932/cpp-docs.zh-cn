---
description: 了解更多： &lt; 字符串 &gt; 运算符
title: '&lt;string&gt; 运算符'
ms.date: 11/04/2016
f1_keywords:
- string/std::operator!=
- string/std::operator&gt;
- string/std::operator&gt;&gt;
- string/std::operator&gt;=
- string/std::operator&lt;
- string/std::operator&lt;&lt;
- string/std::operator&lt;=
- string/std::operator+
- string/std::operator==
ms.assetid: 33ce8f05-06c7-45d3-a0cb-bcd27cf93910
helpviewer_keywords:
- std::operator!= (string)
- std::operator&gt; (string)
- std::operator&gt;&gt; (string)
- std::operator&gt;= (string)
- std::operator&lt; (string)
- std::operator&lt;&lt; (string)
- std::operator&lt;= (string), std::operator== (string)
ms.openlocfilehash: 9a23b4539fbb84533de83a541458deddbd13615e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183706"
---
# <a name="ltstringgt-operators"></a>&lt;string&gt; 运算符

[operator！ =](#op_neq)\
[操作员&gt;](#op_gt)\
[操作员&gt;&gt;](#op_gt_gt)\
[操作员&gt;=](#op_gt_eq)\
[操作员&lt;](#op_lt)\
[操作员&lt;&lt;](#op_lt_lt)\
[操作员&lt;=](#op_lt_eq)\
[operator +](#op_add)\
[operator = =](#op_eq_eq)

## <a name="operator"></a><a name="op_add"></a> operator +

连接两个字符串对象。

```cpp
template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator> operator+(
    const CharType left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>&& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,
    const basic_string<CharType, Traits, Allocator>&& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const basic_string<CharType, Traits, Allocator>&& left,
    CharType right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>&& right);

template <class CharType, class Traits, class Allocator>
basic_string<CharType, Traits, Allocator>&& operator+(
    CharType left,
    const basic_string<CharType, Traits, Allocator>&& right);
```

### <a name="parameters"></a>parameters

*左中*\
要连接的 C 样式字符串或类型 `basic_string` 的对象。

*然后*\
要连接的 C 样式字符串或类型 `basic_string` 的对象。

### <a name="return-value"></a>返回值

是输入字符串的串联的字符串。

### <a name="remarks"></a>备注

函数每个重载 `operator+` 用于将类模板的两个对象连接 [basic_string 类](../standard-library/basic-string-class.md)。 所有有效 `basic_string< CharType, Traits, Allocator>(Left).append(right)` 的返回。 有关详细信息，请参阅 [append](../standard-library/basic-string-class.md#append)。

### <a name="example"></a>示例

```cpp
// string_op_con.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // Declaring an object of type basic_string<char>
   string s1 ( "anti" );
   string s2 ( "gravity" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "heroine";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // Declaring a character constant
   char c1 = '!';
   cout << "The character constant c1 = " << c1 << "." << endl;

   // First member function: concatenates an  object
   // of type basic_string with an object of type basic_string
   string s12 = s1 + s2;
   cout << "The string concatenating s1 & s2 is: " << s12 << endl;

   // Second & fourth member functions: concatenate an object
   // of type basic_string with an object of C-syle string type
   string s1s3 = s1 + s3;
   cout << "The string concatenating s1 & s3 is: " << s1s3 << endl;

   // Third & fifth member functions: concatenate an object
   // of type basic_string with a character constant
   string s1s3c1 = s1s3 + c1;
   cout << "The string concatenating s1 & s3 is: " << s1s3c1 << endl;
}
```

```Output
The basic_string s1 = anti.
The basic_string s2 = gravity.
The C-style string s3 = heroine.
The character constant c1 = !.
The string concatenating s1 & s2 is: antigravity
The string concatenating s1 & s3 is: antiheroine
The string concatenating s1 & s3 is: antiheroine!
```

## <a name="operator"></a><a name="op_neq"></a> operator！ =

测试运算符左侧的字符串对象是否不等于右侧的字符串对象。

```cpp
template <class CharType, class Traits, class Allocator>
bool operator!=(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator!=(
    const basic_string<CharType, Traits, Allocator>& left,
const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator!=(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左中*\
要比较的 C 样式字符串或类型 `basic_string` 的对象。

*然后*\
要比较的 C 样式字符串或类型 `basic_string` 的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的字符串对象不按字典顺序等于右侧的字符串对象，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

列表对象之间的比较基于其元素的字典序比较。 如果两个字符串具有相同的字符数且各自的字符值也相同，则这两个字符串相同。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// string_op_ne.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "pluck" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "pluck";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 != s2 )
      cout << "The strings s1 & s2 are not equal." << endl;
   else
      cout << "The strings s1 & s2 are equal." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s1 != s3 )
      cout << "The strings s1 & s3 are not equal." << endl;
   else
      cout << "The strings s1 & s3 are equal." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type & right-side object of type basic_string
   if ( s3 != s2 )
      cout << "The strings s3 & s2 are not equal." << endl;
   else
      cout << "The strings s3 & s2 are equal." << endl;
}
```

```Output
The basic_string s1 = pluck.
The basic_string s2 = strum.
The C-style string s3 = pluck.
The strings s1 & s2 are not equal.
The strings s1 & s3 are equal.
The strings s3 & s2 are not equal.
```

## <a name="operator"></a><a name="op_eq_eq"></a> operator = =

测试运算符左侧的字符串对象是否等于右侧的字符串对象。

```cpp
template <class CharType, class Traits, class Allocator>
bool operator==(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator==(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator==(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左中*\
要比较的 C 样式字符串或类型 `basic_string` 的对象。

*然后*\
要比较的 C 样式字符串或类型 `basic_string` 的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的字符串对象按字典顺序等于右侧的字符串对象，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

列表对象之间的比较基于其元素的字典序比较。 如果两个字符串具有相同的字符数且各自的字符值也相同，则这两个字符串相同。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// string_op_eq.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "pluck" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "pluck";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 == s2 )
      cout << "The strings s1 & s2 are equal." << endl;
   else
      cout << "The strings s1 & s2 are not equal." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s1 == s3 )
      cout << "The strings s1 & s3 are equal." << endl;
   else
      cout << "The strings s1 & s3 are not equal." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type & right-side object of type basic_string
   if ( s3 == s2 )
      cout << "The strings s3 & s2 are equal." << endl;
   else
      cout << "The strings s3 & s2 are not equal." << endl;
}
```

```Output
The basic_string s1 = pluck.
The basic_string s2 = strum.
The C-style string s3 = pluck.
The strings s1 & s2 are not equal.
The strings s1 & s3 are equal.
The strings s3 & s2 are not equal.
```

## <a name="operatorlt"></a><a name="op_lt"></a> 操作员&lt;

测试运算符左侧的字符串对象是否小于右侧的字符串对象。

```cpp
template <class CharType, class Traits, class Allocator>
bool operator<(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator<(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator<(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左中*\
要比较的 C 样式字符串或类型 `basic_string` 的对象。

*然后*\
要比较的 C 样式字符串或类型 `basic_string` 的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的字符串对象按字典顺序小于右侧的字符串对象，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

字符串之间按字典序逐字符进行比较：

- 如果找到两个不相等的相应字符，则将比较结果作为字符串之间比较的结果。

- 如果找到的所有字符完全相同，但其中一个字符串的字符数要多于另一个字符串的字符数，则将较短的字符串视为小于较长的字符串。

- 如果找到的所有字符完全相同且字符串的字符数也相同，则这两个字符串视为相等。

### <a name="example"></a>示例

```cpp
// string_op_lt.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // Declaring an objects of type basic_string<char>
   string s1 ( "strict" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "strict";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 < s2 )
      cout << "The string s1 is less than the string s2." << endl;
   else
      cout << "The string s1 is not less than the string s2." << endl;

   // Second member function: comparison between left-hand object
   // of type basic_string & right-hand object of C-syle string type
   if ( s1 < s3 )
      cout << "The string s1 is less than the string s3." << endl;
   else
      cout << "The string s1 is not less than the string s3." << endl;

   // Third member function: comparison between left-hand object
   // of C-syle string type & right-hand object of type basic_string
   if ( s3 < s2 )
      cout << "The string s3 is less than the string s2." << endl;
   else
      cout << "The string s3 is not less than the string s2." << endl;
}
```

```Output
The basic_string s1 = strict.
The basic_string s2 = strum.
The C-style string s3 = strict.
The string s1 is less than the string s2.
The string s1 is not less than the string s3.
The string s3 is less than the string s2.
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a> 操作员&lt;=

测试运算符左侧的字符串对象是否小于或等于右侧的字符串对象。

```cpp
template <class CharType, class Traits, class Allocator>
bool operator<=(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator<=(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator<=(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左中*\
要比较的 C 样式字符串或类型 `basic_string` 的对象。

*然后*\
要比较的 C 样式字符串或类型 `basic_string` 的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的字符串对象按字典顺序小于或等于右侧的字符串对象，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

字符串之间按字典序逐字符进行比较：

- 如果找到两个不相等的相应字符，则将比较结果作为字符串之间比较的结果。

- 如果找到的所有字符完全相同，但其中一个字符串的字符数要多于另一个字符串的字符数，则将较短的字符串视为小于较长的字符串。

- 它没找到任何不相等的字符且字符串具有相同数量的字符，则字符串视为相等。

### <a name="example"></a>示例

```cpp
// string_op_le.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "strict" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "strict";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 <= s2 )
      cout << "The string s1 is less than or equal to "
           << "the string s2." << endl;
   else
      cout << "The string s1 is greater than "
           << "the string s2." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s1 <= s3 )
      cout << "The string s1 is less than or equal to "
           << "the string s3." << endl;
   else
      cout << "The string s1 is greater than "
           << "the string s3." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type  & right-side object of type basic_string
   if ( s2 <= s3 )
      cout << "The string s2 is less than or equal to "
           << "the string s3." << endl;
   else
      cout << "The string s2 is greater than "
           << "the string s3." << endl;
}
```

```Output
The basic_string s1 = strict.
The basic_string s2 = strum.
The C-style string s3 = strict.
The string s1 is less than or equal to the string s2.
The string s1 is less than or equal to the string s3.
The string s2 is greater than the string s3.
```

## <a name="operatorltlt"></a><a name="op_lt_lt"></a> 操作员&lt;&lt;

一个模板函数，用于向输出流写入字符串。

```cpp
template <class CharType, class Traits, class Allocator>
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& _Ostr,
    const basic_string<CharType, Traits, Allocator>& str);
```

### <a name="parameters"></a>parameters

*_Ostr*\
正在写入的输出流。

*字符串*\
要输入到输出流的字符串。

### <a name="return-value"></a>返回值

将指定字符串的值写入 *_Ostr* 的输出流中。

### <a name="remarks"></a>备注

模板函数重载 **运算符<<** 将类模板 [basic_string](../standard-library/basic-string-class.md)的对象 *str* 插入到流 *\_ Ostr* 中。 该函数有效返回 `_Ostr.write( str.c_str, str.size )` 。

## <a name="operatorgt"></a><a name="op_gt"></a> 操作员&gt;

测试运算符左侧的字符串对象是否大于右侧的字符串对象。

```cpp
template <class CharType, class Traits, class Allocator>
bool operator>(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator>(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator>(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左中*\
要比较的 C 样式字符串或类型 `basic_string` 的对象。

*然后*\
要比较的 C 样式字符串或类型 `basic_string` 的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的字符串对象按字典顺序大于右侧的字符串对象，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

字符串之间按字典序逐字符进行比较：

- 如果找到两个不相等的相应字符，则将比较结果作为字符串之间比较的结果。

- 如果找到的所有字符完全相同，但其中一个字符串的字符数要多于另一个字符串的字符数，则将较短的字符串视为小于较长的字符串。

- 如果找到的所有字符完全相同且字符串的字符数也相同，则这两个字符串视为相等。

### <a name="example"></a>示例

```cpp
// string_op_gt.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "strict" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "stricture";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 > s2 )
      cout << "The string s1 is greater than "
           << "the string s2." << endl;
   else
      cout << "The string s1 is not greater than "
           << "the string s2." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s3 > s1 )
      cout << "The string s3 is greater than "
           << "the string s1." << endl;
   else
      cout << "The string s3 is not greater than "
           << "the string s1." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type & right-side object of type basic_string
   if ( s2 > s3 )
      cout << "The string s2 is greater than "
           << "the string s3." << endl;
   else
      cout << "The string s2 is not greater than "
           << "the string s3." << endl;
}
```

```Output
The basic_string s1 = strict.
The basic_string s2 = strum.
The C-style string s3 = stricture.
The string s1 is not greater than the string s2.
The string s3 is greater than the string s1.
The string s2 is greater than the string s3.
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a> 操作员&gt;=

测试运算符左侧的字符串对象是否大于或等于右侧的字符串对象。

```cpp
template <class CharType, class Traits, class Allocator>
bool operator>=(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
bool operator>=(
    const basic_string<CharType, Traits, Allocator>& left,
    const CharType* right);

template <class CharType, class Traits, class Allocator>
bool operator>=(
    const CharType* left,
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左中*\
要比较的 C 样式字符串或类型 `basic_string` 的对象。

*然后*\
要比较的 C 样式字符串或类型 `basic_string` 的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的字符串对象按字典顺序大于或等于右侧的字符串对象，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

字符串之间按字典序逐字符进行比较：

- 如果找到两个不相等的相应字符，则将比较结果作为字符串之间比较的结果。

- 如果找到的所有字符完全相同，但其中一个字符串的字符数要多于另一个字符串的字符数，则将较短的字符串视为小于较长的字符串。

- 它没找到任何不相等的字符且字符串具有相同数量的字符，则字符串视为相等。

### <a name="example"></a>示例

```cpp
// string_op_ge.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "strict" );
   string s2 ( "strum" );
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   // Declaring a C-style string
   char *s3 = "stricture";
   cout << "The C-style string s3 = " << s3 << "." << endl;

   // First member function: comparison between left-side object
   // of type basic_string & right-side object of type basic_string
   if ( s1 >= s2 )
      cout << "The string s1 is greater than or equal to "
           << "the string s2." << endl;
   else
      cout << "The string s1 is less than "
           << "the string s2." << endl;

   // Second member function: comparison between left-side object
   // of type basic_string & right-side object of C-syle string type
   if ( s3 >= s1 )
      cout << "The string s3 is greater than or equal to "
           << "the string s1." << endl;
   else
      cout << "The string s3 is less than "
           << "the string s1." << endl;

   // Third member function: comparison between left-side object
   // of C-syle string type & right-side object of type basic_string
   if ( s2 >= s3 )
      cout << "The string s2 is greater than or equal to "
           << "the string s3." << endl;
   else
      cout << "The string s2 is less than "
           << "the string s3." << endl;
}
```

```Output
The basic_string s1 = strict.
The basic_string s2 = strum.
The C-style string s3 = stricture.
The string s1 is less than the string s2.
The string s3 is greater than or equal to the string s1.
The string s2 is greater than or equal to the string s3.
```

## <a name="operatorgtgt"></a><a name="op_gt_gt"></a> 操作员&gt;&gt;

一个模板函数，用于从输入流读取字符串。

```cpp
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& operator>>(
    basic_istream<CharType, Traits>& _Istr,
    basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>parameters

*_Istr*\
用来提取序列的输入流

*然后*\
正在从输入流提取的字符串。

### <a name="return-value"></a>返回值

从 *_Istr* 读取指定字符串的值，并将其返回到 *右侧*。

### <a name="remarks"></a>备注

除非已设置 `skipws` 标志，否则运算符将跳过前导空白字符。 它读取以下所有字符，直到下一个字符是空格或到达文件末尾。

模板函数重载 **运算符>>** 将 *右端* 控制的序列替换为从流 *_Istr* 中提取的一系列元素。 提取将在以下位置停止：

- 在文件结尾。

- 函数提取 `_Istr`. **width** 元素之后（如果该值不为零）。

函数提取 `_Istr`. [max_size](../standard-library/basic-string-class.md#max_size) 元素之后。

- 函数提取 [use_facet](../standard-library/basic-filebuf-class.md#open)ctype 的元素 *ch* <   \< **CharType**> > ( `getloc`) 。 **为** ( **ctype** \< **CharType**> ：： **space**， *ch*) 为 true，在这种情况下，将返回该字符。

如果该函数未提取任何元素，则它将调用 [setstate](../standard-library/basic-ios-class.md#setstate) (`ios_base::failbit`) 。 在任何情况下，函数都会调用 **istr**. **width** (0) 并返回 \* **`this`** 。

### <a name="example"></a>示例

```cpp
// string_op_read_.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string c0;
   cout << "Input a string c0 ( try: Fibonacci numbers ): ";
   cin >> c0;
   cout << "The string entered is c0 = " << c0 << endl;
}
```

## <a name="see-also"></a>请参阅

[\<string>](../standard-library/string.md)
