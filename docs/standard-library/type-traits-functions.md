---
description: 了解详细信息： &lt; type_traits &gt; 函数
title: '&lt;type_traits&gt; 函数'
ms.date: 11/04/2016
ms.assetid: dce4492f-f3e4-4d5e-bdb4-5875321254ec
helpviewer_keywords:
- std::is_assignable
- std::is_copy_assignable
- std::is_copy_constructible
- std::is_default_constructible
- std::is_move_assignable
- std::is_move_constructible
- std::is_nothrow_move_assignable
- std::is_trivially_copy_assignable
- std::is_trivially_move_assignable
- std::is_trivially_move_constructible
ms.openlocfilehash: a1608ddc9d846ca9e8e851ef67d390aebb6f840e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253320"
---
# <a name="lttype_traitsgt-functions"></a>&lt;type_traits&gt; 函数

[is_assignable](#is_assignable)\
[is_copy_assignable](#is_copy_assignable)\
[is_copy_constructible](#is_copy_constructible)\
[is_default_constructible](#is_default_constructible)\
[is_move_assignable](#is_move_assignable)\
[is_move_constructible](#is_move_constructible)\
[is_nothrow_move_assignable](#is_nothrow_move_assignable)\
[is_nothrow_swappable](#is_nothrow_swappable)\
[is_nothrow_swappable_with](#is_nothrow_swappable_with)\
[is_swappable](#is_swappable)\
[is_swappable_with](#is_swappable_with)\
[is_trivially_copy_assignable](#is_trivially_copy_assignable)\
[is_trivially_move_assignable](#is_trivially_move_assignable)\
[is_trivially_move_constructible](#is_trivially_move_constructible)

## <a name="is_assignable"></a><a name="is_assignable"></a> is_assignable

测试 *从* 类型的值是否可以分配 *给类型。*

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>parameters

*自*\
接收赋值的对象的类型。

*从*\
提供值的对象的类型。

### <a name="remarks"></a>备注

未计算的表达式 `declval<To>() = declval<From>()` 必须具有正确格式。 *From* 和 *To* 都必须是完整类型、 **`void`** 或未知绑定的数组。

## <a name="is_copy_assignable"></a><a name="is_copy_assignable"></a> is_copy_assignable

测试是否可以在赋值时复制类型。

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>parameters

*Ty*\
要查询的类型。

### <a name="remarks"></a>备注

如果类型 *Ty* 是具有复制赋值运算符的类，则类型谓词的实例为 true; 否则为 false。 等效于 is_assignable \<Ty&, const Ty&> 。

## <a name="is_copy_constructible"></a><a name="is_copy_constructible"></a> is_copy_constructible

测试类型是否包含复制构造函数。

```cpp
template <class Ty>
struct is_copy_constructible;
```

### <a name="parameters"></a>parameters

*Ty*\
要查询的类型。

### <a name="remarks"></a>备注

如果类型 *Ty* 是具有复制构造函数的类，则类型谓词的实例为 true; 否则为 false。

### <a name="example"></a>示例

```cpp
#include <type_traits>
#include <iostream>

struct Copyable
{
    int val;
};

struct NotCopyable
{
   NotCopyable(const NotCopyable&) = delete;
   int val;

};

int main()
{
    std::cout << "is_copy_constructible<Copyable> == " << std::boolalpha
        << std::is_copy_constructible<Copyable>::value << std::endl;
    std::cout << "is_copy_constructible<NotCopyable> == " << std::boolalpha
        << std::is_copy_constructible<NotCopyable>::value << std::endl;

    return (0);
}
```

```Output
is_copy_constructible<Copyable> == true
is_copy_constructible<NotCopyable > == false
```

## <a name="is_default_constructible"></a><a name="is_default_constructible"></a> is_default_constructible

测试类型是否具有默认构造函数。

```cpp
template <class Ty>
struct is_default_constructible;
```

### <a name="parameters"></a>parameters

*关心*\
要查询的类型。

### <a name="remarks"></a>备注

如果类型 *T* 是具有默认构造函数的类类型，则类型谓词的实例为 true; 否则为 false。 这等效于谓词 `is_constructible<T>`。 类型 *T* 必须是完整类型、 **`void`** 或未知绑定的数组。

### <a name="example"></a>示例

```cpp
#include <type_traits>
#include <iostream>

struct Simple
{
    Simple() : val(0) {}
    int val;
};

struct Simple2
{
    Simple2(int v) : val(v) {}
    int val;
};

int main()
{
    std::cout << "is_default_constructible<Simple> == " << std::boolalpha
        << std::is_default_constructible<Simple>::value << std::endl;
    std::cout << "is_default_constructible<Simple2> == " << std::boolalpha
        << std::is_default_constructible<Simple2>::value << std::endl;

    return (0);
}
```

```Output
is_default_constructible<Simple> == true
is_default_constructible<Simple2> == false
```

## <a name="is_move_assignable"></a><a name="is_move_assignable"></a> is_move_assignable

测试类型是否可移动赋值。

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>parameters

*关心*\
要查询的类型。

### <a name="remarks"></a>备注

如果类型的右值引用可赋予此类型的引用，则该类型可移动赋值。 类型谓词等效于 `is_assignable<T&, T&&>`。 可移动赋值的类型包括可引用的标量类型和类类型，这些类型具有编译器生成的移动赋值运算符或用户定义的移动赋值运算符。

## <a name="is_move_constructible"></a><a name="is_move_constructible"></a> is_move_constructible

测试类型是否具有移动构造函数。

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>parameters

*关心*\
要计算的类型

### <a name="remarks"></a>备注

如果可以使用移动操作构造类型 *T* ，则其计算结果为 true 的类型谓词。 此谓词等效于 `is_constructible<T, T&&>`。

## <a name="is_nothrow_move_assignable"></a><a name="is_nothrow_move_assignable"></a> is_nothrow_move_assignable

测试类型是否具有 **`nothrow`** 移动赋值运算符。

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>parameters

*Ty*\
要查询的类型。

### <a name="remarks"></a>备注

如果类型 *Ty* 具有 nothrow 移动赋值运算符，则类型谓词的实例为 true; 否则为 false。

## <a name="is_nothrow_swappable"></a><a name="is_nothrow_swappable"></a> is_nothrow_swappable

```cpp
template <class T> struct is_nothrow_swappable;
```

## <a name="is_nothrow_swappable_with"></a><a name="is_nothrow_swappable_with"></a> is_nothrow_swappable_with

```cpp
template <class T, class U> struct is_nothrow_swappable_with;
```

## <a name="is_swappable"></a><a name="is_swappable"></a> is_swappable

```cpp
template <class T> struct is_swappable;
```

## <a name="is_swappable_with"></a><a name="is_swappable_with"></a> is_swappable_with

```cpp
template <class T, class U> struct is_swappable_with;
```

## <a name="is_trivially_copy_assignable"></a><a name="is_trivially_copy_assignable"></a> is_trivially_copy_assignable

测试类型是否具有普通复制赋值运算符。

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>parameters

*关心*\
要查询的类型。

### <a name="remarks"></a>备注

如果类型 *T* 是具有普通复制赋值运算符的类，则类型谓词的实例为 true; 否则为 false。

如果类 *t* 的赋值构造函数是隐式提供的，则该类没有虚函数， *类 t 没有* 虚函数，类 *t* 没有虚拟基，类类型的所有非静态数据成员的类具有普通赋值运算符，并且类的类型数组的所有非静态数据成员的类具有普通赋值运算符。

## <a name="is_trivially_move_assignable"></a><a name="is_trivially_move_assignable"></a> is_trivially_move_assignable

测试类型是否具有普通移动赋值运算符。

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>parameters

*Ty*\
要查询的类型。

### <a name="remarks"></a>备注

如果类型 *Ty* 是具有普通移动赋值运算符的类，则类型谓词的实例为 true; 否则为 false。

如果以下情况， *Ty* 类的移动赋值运算符是普通运算符：

它被隐式提供

类 *Ty* 没有虚函数

类 *Ty* 没有虚拟基

类类型的所有非静态数据成员的类具有普通移动赋值运算符

类的类型数组的所有非静态数据成员的类具有普通移动赋值运算符

## <a name="is_trivially_move_constructible"></a><a name="is_trivially_move_constructible"></a> is_trivially_move_constructible

测试类型是否具有普通移动构造函数。

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>parameters

*Ty*\
要查询的类型。

### <a name="remarks"></a>备注

如果类型 *Ty* 是一个具有普通移动构造函数的类，则类型谓词的实例为 true; 否则为 false。

如果以下情况， *Ty* 类的移动构造函数是普通的：

它被隐式声明

其参数类型等效于那些隐式声明的参数类型

类 *Ty* 没有虚函数

类 *Ty* 没有虚拟基

类没有任何不稳定的非静态数据成员

类 *Ty* 的所有直接基都具有普通的移动构造函数

类类型的所有非静态数据成员的类具有普通构造函数

类的类型数组的所有非静态数据成员的类具有普通构造函数

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)
