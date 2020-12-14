---
description: 了解有关以下内容的详细信息： vector &lt; bool &gt; 类
title: vector&lt;bool&gt; 类
ms.date: 11/04/2016
f1_keywords:
- vector<bool>
- vector/std::vector::flip
helpviewer_keywords:
- std::vector [C++], const_pointer
- std::vector [C++], const_reference
- std::vector [C++], pointer
- std::vector [C++], flip
- std::vector [C++], swap
ms.assetid: 8028c8ed-ac9c-4f06-aba1-5de45c00aafb
ms.openlocfilehash: ecc7c083825a92aca429f9418d35ff9d4cf7dcca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280503"
---
# <a name="vectorltboolgt-class"></a>vector&lt;bool&gt; 类

`vector<bool>`类是类型的元素的 [矢量](../standard-library/vector-class.md)的部分专用化 **`bool`** 。 它具有用于专用化的基础类型的分配器，此分配器通过每个位存储一个值来提供空间优化 **`bool`** 。

## <a name="syntax"></a>语法

```cpp
template <class Allocator = allocator<bool>>
class vector<bool, Allocator>
```

## <a name="remarks"></a>备注

除了本文中说明的差异以外，此类模板专用化的行为类似于矢量。

处理类型的操作 **`bool`** 与容器存储中的值相对应。 `allocator_traits::construct` 不用于构造这些值。

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[const_pointer](#const_pointer)|`const_iterator` 的 typedef，可用作指向 `vector<bool>` 的布尔值元素的常量指针。|
|[const_reference](#const_reference)|的 typedef **`bool`** 。 初始化之后，它不观察对原始值的更新。|
|[变为](#pointer)|`iterator` 的 typedef，可用作指向 `vector<bool>` 的布尔值元素的指针。|

### <a name="member-functions"></a>成员函数

|成员函数|说明|
|-|-|
|[flip](#flip)|反转 `vector<bool>` 中的所有位。|
|[swap](#swap)|交换两个 `vector<bool>` 的元素。|
|[operator&#91;&#93;](#op_at)|返回对指定位置的 `vector<bool>` 元素的模拟引用。|
|`at`|函数与非专用化 [vector](../standard-library/vector-class.md)：： at 函数相同，只不过它使用代理类 [vector \<bool> ：： reference](#reference_class)。 另请参阅 [operator[]](#op_at)。|
|`front`|函数与非专用化 [vector](../standard-library/vector-class.md)：： front 函数相同，不同之处在于它使用代理类 [vector \<bool> ：： reference](#reference_class)。 另请参阅 [operator[]](#op_at)。|
|`back`|除了使用代理类[vector \<bool> ：： reference](#reference_class)以外，函数与非专用化[vector](../standard-library/vector-class.md)：： back 函数相同。 另请参阅 [operator[]](#op_at)。|

### <a name="proxy-class"></a>代理类

|名称|描述|
|-|-|
|[vector \<bool> 引用类](#reference_class)|一种用做代理以模拟 `bool&` 行为的类，其对象可提供对 `vector<bool>` 对象中的元素（一位）的引用。|

## <a name="requirements"></a>要求

**标头**： \<vector>

**命名空间:** std

## <a name="vectorboolconst_pointer"></a><a name="const_pointer"></a> vector \<bool> ：： const_pointer

该类型描述可作为常量指针的对象，该指针指向 `vector<bool>` 对象所包含序列中的布尔元素。

```cpp
typedef const_iterator const_pointer;
```

## <a name="vectorboolconst_reference"></a><a name="const_reference"></a> vector \<bool> ：： const_reference

该类型描述可作为常量引用的对象，它引用 `vector<bool>` 对象所包含序列中的布尔元素。

```cpp
typedef bool const_reference;
```

### <a name="remarks"></a>备注

有关详细信息和代码示例，请参阅 [vector&lt;bool&gt;::reference::operator=](#reference_operator_eq)。

## <a name="vectorboolflip"></a><a name="flip"></a> vector \<bool> ：： flip

反转 `vector<bool>` 中的所有位。

```cpp
void flip();
```

### <a name="example"></a>示例

```cpp
// vector_bool_flip.cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha; // format output for subsequent code

    vector<bool> vb = { true, false, false, true, true };
    cout << "The vector is:" << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;

    vb.flip();

    cout << "The flipped vector is:" << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;
}
```

## <a name="vectorbooloperator"></a><a name="op_at"></a> vector \<bool> ：： operator []

返回对指定位置的 `vector<bool>` 元素的模拟引用。

```cpp
vector<bool>::reference operator[](size_type Pos);

vector&<bool&>::const_reference operator[](size_type Pos) const;
```

### <a name="parameters"></a>parameters

*位置*\
`vector<bool>` 元素的位置。

### <a name="return-value"></a>返回值

一个 [vector \<bool> ：： reference](#reference_class) 或 [vector \<bool> ：： const_reference](#const_reference) 对象，其中包含索引元素的值。

如果指定的位置大于或等于容器大小，则结果为 undefined。

### <a name="remarks"></a>备注

如果使用 _ITERATOR_DEBUG_LEVEL 集进行编译，则当你尝试访问矢量边界之外的元素时，将发生运行时错误。  有关更多信息，请参见 [Checked Iterators](../standard-library/checked-iterators.md)。

### <a name="example"></a>示例

此代码示例演示如何正确使用 `vector<bool>::operator[]` 和两个常见编码错误（注释掉）。这些错误会导致错误，因为 `vector<bool>::reference` 无法获取返回的对象的地址 `vector<bool>::operator[]` 。

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha;
    vector<bool> vb;

    vb.push_back(true);
    vb.push_back(false);

    //    bool* pb = &vb[1]; // conversion error - do not use
    //    bool& refb = vb[1];   // conversion error - do not use
    bool hold = vb[1];
    cout << "The second element of vb is " << vb[1] << endl;
    cout << "The held value from the second element of vb is " << hold << endl;

    // Note this doesn't modify hold.
    vb[1] = true;
    cout << "The second element of vb is " << vb[1] << endl;
    cout << "The held value from the second element of vb is " << hold << endl;
}
```

## <a name="vectorboolpointer"></a><a name="pointer"></a> vector \<bool> ：:p ointer

一种类型，用于描述一个对象来充当指针，以便指向 `vector<bool>` 对象所包含序列的布尔元素。

```cpp
typedef iterator pointer;
```

## <a name="vectorboolreference-class"></a><a name="reference_class"></a> vector \<bool> ：： Reference 类

`vector<bool>::reference`类是由[vector \<bool> 类](../standard-library/vector-bool-class.md)提供的用于模拟的代理类 `bool&` 。

### <a name="remarks"></a>备注

必须使用模拟引用，因为 C++ 不允许直接引用位。 `vector<bool>` 每个元素只使用一个位，这可以使用此代理类来引用。 但是，引用模拟不会完成，原因是某些赋值无效。 例如，由于 `vector<bool>::reference` 无法采用对象的地址，因此，以下使用 [vector \<bool> ：： operator&#91;&#93;](#op_at) 的代码不正确：

```cpp
vector<bool> vb;
//...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

### <a name="vectorboolreferenceflip"></a><a name="reference_flip"></a> vector \<bool> ：： reference：： flip

反转所引用[矢量 \<bool> ](../standard-library/vector-bool-class.md)元素的布尔值。

```cpp
void flip();
```

#### <a name="example"></a>示例

```cpp
// vector_bool_ref_flip.cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha;

    vector<bool> vb = { true, false, false, true, true };

    cout << "The vector is: " << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;

    vector<bool>::reference vbref = vb.front();
    vbref.flip();

    cout << "The vector with first element flipped is: " << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;
}
```

```Output
The vector is:
    true false false true true
The vector with first element flipped is:
    false false false true true
```

### <a name="vectorboolreferenceoperator-bool"></a><a name="reference_operator_bool"></a> vector \<bool> ：： reference：： operator bool

提供从到的隐式转换 `vector<bool>::reference` **`bool`** 。

```cpp
operator bool() const;
```

#### <a name="return-value"></a>返回值

Vector 对象的元素的布尔值 \<bool> 。

#### <a name="remarks"></a>备注

`vector<bool>` 对象无法通过此运算符修改。

### <a name="vectorboolreferenceoperator"></a><a name="reference_operator_eq"></a> vector \<bool> ：： reference：： operator =

将布尔值赋给一个位，或将引用的元素所保存的值赋给一个位。

```cpp
reference& operator=(const reference& Right);
reference& operator=(bool Val);
```

### <a name="parameters"></a>parameters

*然后*\
要将值赋给位的元素引用。

*初始值*\
要赋给位的布尔值。

#### <a name="example"></a>示例

```cpp
// vector_bool_ref_op_assign.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    cout << boolalpha;

    vector<bool> vb = { true, false, false, true, true };

    print("The vector is: ", vb);

    // Invoke vector<bool>::reference::operator=()
    vector<bool>::reference refelem1 = vb[0];
    vector<bool>::reference refelem2 = vb[1];
    vector<bool>::reference refelem3 = vb[2];

    bool b1 = refelem1;
    bool b2 = refelem2;
    bool b3 = refelem3;
    cout << "The original value of the 1st element stored in a bool: " << b1 << endl;
    cout << "The original value of the 2nd element stored in a bool: " << b2 << endl;
    cout << "The original value of the 3rd element stored in a bool: " << b3 << endl;
    cout << endl;

    refelem2 = refelem1;

    print("The vector after assigning refelem1 to refelem2 is now: ", vb);

    refelem3 = true;

    print("The vector after assigning false to refelem1 is now: ", vb);

    // The initial values are still stored in the bool variables and remained unchanged
    cout << "The original value of the 1st element still stored in a bool: " << b1 << endl;
    cout << "The original value of the 2nd element still stored in a bool: " << b2 << endl;
    cout << "The original value of the 3rd element still stored in a bool: " << b3 << endl;
    cout << endl;
}
```

```Output
The vector is: true false false true true
The original value of the 1st element stored in a bool: true
The original value of the 2nd element stored in a bool: false
The original value of the 3rd element stored in a bool: false

The vector after assigning refelem1 to refelem2 is now: true true false true true
The vector after assigning false to refelem1 is now: true true true true true
The original value of the 1st element still stored in a bool: true
The original value of the 2nd element still stored in a bool: false
The original value of the 3rd element still stored in a bool: false
```

## <a name="vectorboolswap"></a><a name="swap"></a> vector \<bool> ：： swap

`vector<bool>`通过使用代理类[vector \<bool> ：： Reference](#reference_class)来交换布尔向量的两个元素 () 的静态成员函数。

```cpp
static void swap(
    reference Left,
    reference Right);
```

### <a name="parameters"></a>parameters

*左中*\
要与 *右侧* 元素交换的元素。

*然后*\
要与 *左侧* 元素交换的元素。

### <a name="remarks"></a>备注

此重载支持 `vector<bool>` 的特殊代理要求。 [vector](../standard-library/vector-class.md)::swap 的功能与 `vector<bool>::swap()` 的单参数重载相同。

## <a name="see-also"></a>请参阅

[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 标准库参考](../standard-library/cpp-standard-library-reference.md)
