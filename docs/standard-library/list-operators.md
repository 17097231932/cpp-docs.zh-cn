---
description: 了解详细信息： &lt; 列出 &gt; 操作员
title: '&lt;list&gt; 运算符'
ms.date: 11/04/2016
f1_keywords:
- list/std::operator!=
- list/std::operator&gt;
- list/std::operator&gt;=
- list/std::operator&lt;
- list/std::operator&lt;=
- list/std::operator==
ms.assetid: 8103d8f2-c30f-49ad-ac50-b3ba6a907ebe
helpviewer_keywords:
- std::operator!= (list)
- std::operator&gt; (list)
- std::operator&gt;= (list)
- std::operator&lt; (list)
- std::operator&lt;= (list)
- std::operator== (list)
ms.openlocfilehash: 86f032a201943e6b42a997c2fc6ff29df353351e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284689"
---
# <a name="ltlistgt-operators"></a>&lt;list&gt; 运算符

## <a name="operator"></a><a name="op_neq"></a> operator！ =

测试运算符左侧的列表对象是否不等于右侧的列表对象。

```cpp
bool operator!=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左中*\
一个 `list` 类型的对象。

*然后*\
一个 `list` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果列表不相等，则为; **`false`** 如果列表相等，则为。

### <a name="remarks"></a>备注

列表对象之间的比较基于其元素的成对比较。 如果两个列表具有的元素数目相等且对应元素具有相同的值，则两个列表相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// list_op_ne.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
using namespace std;
list <int> c1, c2;
c1.push_back( 1 );
c2.push_back( 2 );

if ( c1 != c2 )
cout << "Lists not equal." << endl;
else
cout << "Lists equal." << endl;
}
/* Output:
Lists not equal.
*/
```

## <a name="operatorlt"></a><a name="op_lt"></a> 操作员&lt;

测试运算符左侧的列表对象是否小于右侧的列表对象。

```cpp
bool operator<(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左中*\
一个 `list` 类型的对象。

*然后*\
一个 `list` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的列表小于但不等于运算符右侧的列表，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

列表对象之间的比较基于其元素的成对比较。 两个对象之间的小于关系基于首对不相等元素之间的比较。

### <a name="example"></a>示例

```cpp
// list_op_lt.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 < c2 )
      cout << "List c1 is less than list c2." << endl;
   else
      cout << "List c1 is not less than list c2." << endl;
}
/* Output:
List c1 is less than list c2.
*/
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a> 操作员&lt;=

测试运算符左侧的列表对象是否小于或等于右侧的列表对象。

```cpp
bool operator<=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左中*\
一个 `list` 类型的对象。

*然后*\
一个 `list` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的列表小于或等于运算符右侧的列表，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

列表对象之间的比较基于其元素的成对比较。 两个对象之间的小于或等于关系基于首对不相等元素的比较。

### <a name="example"></a>示例

```cpp
// list_op_le.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 <= c2 )
      cout << "List c1 is less than or equal to list c2." << endl;
   else
      cout << "List c1 is greater than list c2." << endl;
}
/* Output:
List c1 is less than or equal to list c2.
*/
```

## <a name="operator"></a><a name="op_eq_eq"></a> operator = =

测试运算符左侧的列表对象是否等于右侧的列表对象。

```cpp
bool operator==(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左中*\
一个 `list` 类型的对象。

*然后*\
一个 `list` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的列表等于运算符右侧的列表，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

列表对象之间的比较基于其元素的成对比较。 如果两个列表具有的元素数目相等且对应元素具有相同的值，则两个列表相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// list_op_eq.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
int main( )
{
   using namespace std;

   list <int> c1, c2;
   c1.push_back( 1 );
   c2.push_back( 1 );

   if ( c1 == c2 )
      cout << "The lists are equal." << endl;
   else
      cout << "The lists are not equal." << endl;
}
/* Output:
The lists are equal.
*/
```

## <a name="operatorgt"></a><a name="op_gt"></a> 操作员&gt;

测试运算符左侧的列表对象是否大于右侧的列表对象。

```cpp
bool operator>(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左中*\
一个 `list` 类型的对象。

*然后*\
一个 `list` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的列表大于运算符右侧的列表，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

列表对象之间的比较基于其元素的成对比较。 两个对象之间的大于关系基于首对不相等元素之间的比较。

### <a name="example"></a>示例

```cpp
// list_op_gt.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 > c2 )
      cout << "List c1 is greater than list c2." << endl;
   else
      cout << "List c1 is not greater than list c2." << endl;
}
/* Output:
List c1 is greater than list c2.
*/
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a> 操作员&gt;=

测试运算符左侧的列表对象是否大于或等于右侧的列表对象。

```cpp
bool operator>=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左中*\
一个 `list` 类型的对象。

*然后*\
一个 `list` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的列表大于或等于运算符右侧的列表，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

列表对象之间的比较基于其元素的成对比较。 两个对象之间大于或等于的关系基于首对不相等元素之间的比较。

### <a name="example"></a>示例

```cpp
// list_op_ge.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 >= c2 )
      cout << "List c1 is greater than or equal to list c2." << endl;
   else
      cout << "List c1 is less than list c2." << endl;
}
/* Output:
List c1 is greater than or equal to list c2.
*/
```
