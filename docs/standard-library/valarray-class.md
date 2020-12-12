---
description: 了解详细信息： valarray 类
title: valarray 类
ms.date: 03/27/2019
f1_keywords:
- valarray/std::valarray
- valarray/std::valarray::value_type
- valarray/std::valarray::apply
- valarray/std::valarray::cshift
- valarray/std::valarray::free
- valarray/std::valarray::max
- valarray/std::valarray::min
- valarray/std::valarray::resize
- valarray/std::valarray::shift
- valarray/std::valarray::size
- valarray/std::valarray::sum
- valarray/std::valarray::swap
helpviewer_keywords:
- std::valarray [C++]
- std::valarray [C++], value_type
- std::valarray [C++], apply
- std::valarray [C++], cshift
- std::valarray [C++], free
- std::valarray [C++], max
- std::valarray [C++], min
- std::valarray [C++], resize
- std::valarray [C++], shift
- std::valarray [C++], size
- std::valarray [C++], sum
- std::valarray [C++], swap
ms.assetid: 19b862f9-5d09-4003-8844-6ddd02c1a3a7
ms.openlocfilehash: 53b2c2160b522bd28e316eb29f0661447fb84b11
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132621"
---
# <a name="valarray-class"></a>valarray 类

类模板描述了一个对象，该对象控制类型的元素的序列 `Type` ，这些元素存储为数组，旨在执行高速数学运算，并针对计算性能进行了优化。

## <a name="remarks"></a>备注

此类是一组有序值的数学概念表示形式，元素从 0 开始按顺序编号。 此类描述为一个近容器，因为它支持一些（并非所有）第一类序列容器（如 [vector](../standard-library/vector-class.md)）支持的功能。 它在以下两个重要方面不同于类模板向量：

- 它定义了相同类型和长度对象的相应元素之间的众多算术运算 `valarray<Type>` ，如 *xarr* = cos ( *yarr*) + sin ( *zarr*) 。

- 它 `valarray<Type>` 通过重载 [运算符&#91;&#93;](#op_at)来定义用于为对象进行下标的各种有趣的方法。

类的对象 `Type` ：

- 具有公共默认构造函数、析构函数、复制构造函数、赋值运算符和常规行为。

- 根据需要，定义适用于浮点类型的算术运算符、数学函数和常规行为。

具体而言，复制构造和后跟分配的默认构造之间可能不存在任何细微的差异。 对类的对象的操作都 `Type` 不会引发异常。

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|名称|描述|
|-|-|
|[valarray](#valarray)|构造一个 ，其具有特定大小、包含特定值的元素、作为另一个 的副本或另一个  的子集。|

### <a name="typedefs"></a>Typedef

|名称|描述|
|-|-|
|[value_type](#value_type)|一种类型，表示存储在 `valarray` 中的元素的类型。|

### <a name="functions"></a>函数

|名称|描述|
|-|-|
|[应用](#apply)|将指定函数应用到 `valarray` 的每个元素。|
|[cshift](#cshift)|将 `valarray` 中的所有元素循环移动指定数目的位置。|
|[free](#free)|释放 `valarray` 使用的内存。|
|[max](#max)|查找 `valarray` 中的最大元素。|
|[min](#min)|查找 `valarray` 中的最小元素。|
|[调节](#resize)|将 `valarray` 中元素的数量更改为指定数量，根据需要添加或删除元素。|
|[shift](#shift)|将 `valarray` 的所有元素移动指定数目的位置。|
|[大小](#size)|查找 `valarray` 中的元素数目。|
|[sum](#sum)|确定长度不为零的 `valarray` 中的所有元素的总和。|
|[swap](#swap)||

### <a name="operators"></a>运算符

|名称|描述|
|-|-|
|[操作员!](#op_not)|一个一元运算符，它用于获取 `valarray` 中每个元素的逻辑 `NOT` 值。|
|[运算符% =](#op_mod_eq)|获取用指定 `valarray` 或元素类型的值对数组元素进行点除所得的余数。|
|[运算符&=](#op_and_eq)|获取数组中元素的按位 `AND`，该数组具有指定 `valarray` 中的对应元素或具有元素类型的值。|
|[运算符>>=](#op_gt_gt_eq)|将 `valarray` 操作数中的每个元素向右移动指定数目的位置，或者按第二个 `valarray` 指定的点算数右移。|
|[运算符<<=](#op_lt_lt_eq)|将 `valarray` 操作数中的每个元素向左移动指定数目的位置，或者按第二个 `valarray` 指定的点算数左移。|
|[运算符 * =](#op_star_eq)|将指定 `valarray` 的元素或元素类型的值与操作数 `valarray` 进行点乘。|
|[operator +](#op_add)|一个一元运算符，该运算符将 `valarray` 中的所有元素相加。|
|[运算符 + =](#op_add_eq)|将指定 `valarray` 的元素或元素类型的值与操作数 `valarray` 进行点加。|
|[操作员](#operator-)|一个一元运算符，该运算符将 `valarray` 中的所有元素相减。|
|[operator-=](#operator-_eq)|将指定 `valarray` 的元素或元素类型的值与操作数 `valarray` 进行点减。|
|[operator/=](#op_div_eq)|将操作数 `valarray` 与指定 `valarray` 的元素或元素类型的值进行点除。|
|[operator =](#op_eq)|将元素分配给 `valarray`，其值可以直接指定，也可以作为一些其他 `valarray` 的一部分指定，或由 `slice_array`、`gslice_array`、`mask_array` 或 `indirect_array` 指定。|
|[operator&#91;&#93;](#op_at)|返回对指定索引或指定子集处的元素或其值的引用。|
|[operator ^ =](#op_xor_eq)|获取数组与指定 valarray 或元素类型的值进行的按点排除逻辑或运算符 (`XOR`)。|
|[运算符&#124;=](#op_or_eq)|获取数组中元素的按位 `OR`，该数组具有指定 `valarray` 中的对应元素或具有元素类型的值。|
|[运算符 ~](#op_dtor)|一个一元运算符，该运算符获取 `valarray` 中每个元素的按位 `NOT` 值。|

## <a name="apply"></a><a name="apply"></a> 应用

将指定函数应用到 valarray 的每个元素。

```cpp
valarray<Type> apply(Type _Func(Type)) const;

valarray<Type> apply(Type _Func(constType&)) const;
```

### <a name="parameters"></a>parameters

*(类型 _Func)*\
函数对象将应用于操作数 valarray 的每个元素。

*_Func (const 类型&)*\
const 的函数对象将应用于操作数 valarray 的每个元素。

### <a name="return-value"></a>返回值

一个 valarray，它的元素已使 `_Func` 将点算应用到操作数 valarray 的元素。

### <a name="remarks"></a>备注

此成员函数返回 valarray 类的对象 [](../standard-library/valarray-class.md) **\<Type>** ，其 [大小](#size)为，其中每个元素都是 `_Func((*this)[I])` 。

### <a name="example"></a>示例

```cpp
// valarray_apply.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

using namespace std;

int __cdecl MyApplyFunc( int n )
{
   return n*2;
}

int main( int argc, char* argv[] )
{
   valarray<int> vaR(10), vaApplied(10);
   int i;

   for ( i = 0; i < 10; i += 3 )
      vaR[i] = i;

   for ( i = 1; i < 10; i += 3 )
      vaR[i] = 0;

   for ( i = 2; i < 10; i += 3 )
      vaR[i] = -i;

   cout << "The initial Right valarray is: (";
   for   ( i=0; i < 10; ++i )
      cout << " " << vaR[i];
   cout << " )" << endl;

   vaApplied = vaR.apply( MyApplyFunc );

   cout << "The element-by-element result of "
       << "applying MyApplyFunc to vaR is the\nvalarray: ( ";
   for ( i = 0; i < 10; ++i )
      cout << " " << vaApplied[i];
   cout << " )" << endl;
}
```

```Output
The initial Right valarray is: ( 0 0 -2 3 0 -5 6 0 -8 9 )
The element-by-element result of applying MyApplyFunc to vaR is the
valarray: (  0 0 -4 6 0 -10 12 0 -16 18 )
```

## <a name="cshift"></a><a name="cshift"></a> cshift

将 valarray 中的所有元素以指定位数循环移动。

```cpp
valarray<Type> cshift(int count) const;
```

### <a name="parameters"></a>parameters

*计*\
要向前移动元素的位数。

### <a name="return-value"></a>返回值

一个新的 valarray，其中所有元素都 *已移动到* valarray 前面的位置循环，相对于它们在操作数 valarray 中的位置。

### <a name="remarks"></a>备注

正值 of *count* 将元素循环左 *计数* 位置。

*计数* 的负值会使元素循环右 *计数* 位置。

### <a name="example"></a>示例

```cpp
// valarray_cshift.cpp
// compile with: /EHsc

#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;

    valarray<int> va1(10), va2(10);
    for (i = 0; i < 10; i+=1)
        va1[i] = i;
    for (i = 0; i < 10; i+=1)
        va2[i] = 10 - i;

    cout << "The operand valarray va1 is: (";
    for (i = 0; i < 10; i++)
        cout << " " << va1[i];
    cout << ")" << endl;

    // A positive parameter shifts elements right
    va1 = va1.cshift(4);
    cout << "The cyclically shifted valarray va1 is:\nva1.cshift (4) = (";
    for (i = 0; i < 10; i++)
        cout << " " << va1[i];
    cout << ")" << endl;

    cout << "The operand valarray va2 is: (";
    for (i = 0; i < 10; i++)
        cout << " " << va2[i];
    cout << ")" << endl;

    // A negative parameter shifts elements left
    va2 = va2.cshift(-4);
    cout << "The cyclically shifted valarray va2 is:\nva2.shift (-4) = (";
    for (i = 0; i < 10; i++)
        cout << " " << va2[i];
    cout << ")" << endl;
}
```

```Output
The operand valarray va1 is: ( 0 1 2 3 4 5 6 7 8 9)
The cyclically shifted valarray va1 is:
va1.cshift (4) = ( 4 5 6 7 8 9 0 1 2 3)
The operand valarray va2 is: ( 10 9 8 7 6 5 4 3 2 1)
The cyclically shifted valarray va2 is:
va2.shift (-4) = ( 4 3 2 1 10 9 8 7 6 5)
```

## <a name="free"></a><a name="free"></a> 忙

释放 valarray 使用的内存。

```cpp
void free();
```

### <a name="remarks"></a>备注

此非标准函数等效于分配空 valarray。 例如：

```cpp
valarray<T> v;
v = valarray<T>();

// equivalent to v.free()
```

## <a name="max"></a><a name="max"></a> 数量

查找 valarray 中的最大元素。

```cpp
Type max() const;
```

### <a name="return-value"></a>返回值

操作数 valarray 中的元素最大值。

### <a name="remarks"></a>备注

成员函数通过在类的元素对之间应用 **运算符 \<** or **operator>** 来比较值 `Type` ，必须为元素提供运算符 `Type` 。

### <a name="example"></a>示例

```cpp
// valarray_max.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i, MaxValue;

   valarray<int> vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  2*i - 1;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  10 - i;

   cout << "The operand valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   MaxValue = vaR.max (  );
   cout << "The largest element in the valarray is: "
        << MaxValue  << "." << endl;
}
```

```Output
The operand valarray is: ( 0 1 8 3 7 5 6 13 2 9 ).
The largest element in the valarray is: 13.
```

## <a name="min"></a><a name="min"></a> 分钟

查找 valarray 中的最小元素。

```cpp
Type min() const;
```

### <a name="return-value"></a>返回值

操作数 valarray 中的元素最小值。

### <a name="remarks"></a>备注

成员函数通过在类的元素对之间应用 **运算符 \<** or **operator>** 来比较值 `Type` ，必须为元素提供运算符 `Type` 。

### <a name="example"></a>示例

```cpp
// valarray_min.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i, MinValue;

   valarray<int> vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  2*i;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  5 - i;

   cout << "The operand valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   MinValue = vaR.min ( );
   cout << "The smallest element in the valarray is: "
        << MinValue  << "." << endl;
}
/* Output:
The operand valarray is: ( 0 2 3 -3 8 0 -6 14 -3 -9 ).
The smallest element in the valarray is: -9.
*/
```

## <a name="operator"></a><a name="op_not"></a> 操作员!

一个一元运算符，该运算符获取 valarray 中每个元素的逻辑 **NOT** 值。

```cpp
valarray<bool> operator!() const;
```

### <a name="return-value"></a>返回值

布尔值的 valarray，这些布尔值表示操作数 valarray 的元素值的求反运算。

### <a name="remarks"></a>备注

逻辑运算 **NOT** 将对元素进行求反，因为它会将所有零值转换为一个整体，将所有非零值视为一个整体，然后将它们转换为零值。 布尔值的返回 valarray 的大小与操作数 valarray 相同。

还有一个按位 **not**[valarray：： operator ~](#op_dtor) 对 valarray 的二进制表示形式中的单个位进行求反 **`char`** **`int`** 。

### <a name="example"></a>示例

```cpp
// valarray_op_lognot.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 );
   valarray<bool> vaNOT ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;

   cout << "The initial valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   vaNOT = !vaL;
   cout << "The element-by-element result of "
        << "the logical NOT operator! is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNOT [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The element-by-element result of the logical NOT operator! is the
valarray: ( 1 1 1 0 1 0 1 0 1 0 ).
```

## <a name="operator"></a><a name="op_mod_eq"></a> 运算符% =

获取用指定 valarray 或元素类型的值对数组元素进行点除所得的余数。

```cpp
valarray<Type>& operator%=(const valarray<Type>& right);

valarray<Type>& operator%=(const Type& right);
```

### <a name="parameters"></a>parameters

*然后*\
valarray 或值与操作数 valarray 的 valarray 或值相同的元素类型，用于对操作数 valarray 进行点除。

### <a name="return-value"></a>返回值

一个 valarray，其元素是从操作数 *的按 valarray*

### <a name="example"></a>示例

```cpp
// valarray_class_op_rem.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 6 ), vaR ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  53;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -67;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  3*i+1;

   cout << "The initial valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial  right valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL %= vaR;
   cout << "The remainders from the element-by-element "
        << "division is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is: ( 53 -67 53 -67 53 -67 ).
The initial  right valarray is: ( 1 4 7 10 13 16 ).
The remainders from the element-by-element division is the
valarray: ( 0 -3 4 -7 1 -3 ).
```

## <a name="operatoramp"></a><a name="op_and_eq"></a> 操作员&amp;=

获取数组中元素的按位 **AND**，该数组具有指定 valarray 中的对应元素或具有元素类型的值。

```cpp
valarray<Type>& operator&=(const valarray<Type>& right);

valarray<Type>& operator&=(const Type& right);
```

### <a name="parameters"></a>parameters

*然后*\
元素类型的 valarray 或值与操作数 valarray 的值相同，后者是按逻辑 `AND` 与操作数 valarray 一起使用的。

### <a name="return-value"></a>返回值

一个 valarray，其元素是 `AND` 操作数 valarray *右侧* 的按元素逻辑

### <a name="remarks"></a>备注

按位运算仅可用于操作和数据类型中的位和 **`char`** **`int`** 变体，不能用于 **`float`** 、 **`double`** 、 **longdouble**、 **`void`** 、 **`bool`** 或其他更复杂的数据类型。

按位 AND 具有与逻辑相同的事实数据表， `AND` 但适用于单个位级别上的数据类型。 如果有位 *b* 1 和 *b* 2，则 *b* 1 `AND` *b* 2 为 **`true`** true; 如果至少有一个位为 false，则为 **`false`** 。

### <a name="example"></a>示例

```cpp
// valarray_class_op_bitand.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL &= vaR;
   cout << "The element-by-element result of "
        << "the logical AND operator&= is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the logical AND operator&= is the
valarray: ( 0 0 0 2 0 4 0 6 0 8 ).
```

## <a name="operatorgtgt"></a><a name="op_gt_gt_eq"></a> 操作员&gt;&gt;=

将 valarray 操作数的每个元素的位以指定数位向右移动，或按由第二个 valarray 指定的元素指向值向右移位。

```cpp
valarray<Type>& operator>>=(const valarray<Type>& right);

valarray<Type>& operator>>=(const Type& right);
```

### <a name="parameters"></a>parameters

*然后*\
指示右移位数或 valarray（其元素指示右移的元素指向值）。

### <a name="return-value"></a>返回值

一个 valarray，其元素已移动到 *右侧* 指定的量。

### <a name="remarks"></a>备注

有符号的数字必须保留其符号。

### <a name="example"></a>示例

```cpp
// valarray_class_op_rs.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  64;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -64;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial operand valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The  right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL >>= vaR;
   cout << "The element-by-element result of "
        << "the right shift is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial operand valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the right shift is the
valarray: ( 64 -32 16 -8 4 -2 1 -1 ).
```

## <a name="operatorltlt"></a><a name="op_lt_lt_eq"></a> 操作员&lt;&lt;=

将 valarray 操作数的每个元素的位以指定数位向右移动，或按由第二个 valarray 指定的元素指向值向左移位。

```cpp
valarray<Type>& operator<<=(const valarray<Type>& right);

valarray<Type>& operator<<=(const Type& right);
```

### <a name="parameters"></a>parameters

*然后*\
指示左移位数或 valarray（其元素指示左移的元素指向值）。

### <a name="return-value"></a>返回值

一个 valarray，其元素已向左移动 *右侧* 指定的量。

### <a name="remarks"></a>备注

有符号的数字必须保留其符号。

### <a name="example"></a>示例

```cpp
// valarray_class_op_ls.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial operand valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The  right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL <<= vaR;
   cout << "The element-by-element result of "
        << "the left shift"
        << endl << "on the operand array is the valarray:"
        << endl << "( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial operand valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the left shift
on the operand array is the valarray:
( 1 -2 4 -8 16 -32 64 -128 ).
```

## <a name="operator"></a><a name="op_star_eq"></a> 运算符 * =

将指定 valarray 的元素或元素类型的值与操作数 valarray 进行点乘。

```cpp
valarray<Type>& operator*=(const valarray<Type>& right);

valarray<Type>& operator*=(const Type& right);
```

### <a name="parameters"></a>parameters

*然后*\
valarray 或值与操作数 valarray 的 valarray 或值相同的元素类型，用于对操作数 valarray 进行点乘。

### <a name="return-value"></a>返回值

一个 valarray，其元素是操作数 valarray 和 *right* 的面向元素的积。

### <a name="example"></a>示例

```cpp
// valarray_op_emult.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL *= vaR;
   cout << "The element-by-element result of "
        << "the multiplication is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
/* Output:
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the multiplication is the
valarray: ( 0 -1 4 -3 8 -5 12 -7 ).
*/
```

## <a name="operator"></a><a name="op_add"></a> operator +

一个一元运算符，该运算符将 valarray 中的所有元素相加。

```cpp
valarray<Type> operator+() const;
```

### <a name="return-value"></a>返回值

一个 valarray，它的元素是操作数数列的元素的和。

### <a name="example"></a>示例

```cpp
// valarray_op_eplus.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 );
   valarray<int> vaPLUS ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;

   cout << "The initial valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   vaPLUS = +vaL;
   cout << "The element-by-element result of "
        << "the operator+ is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaPLUS [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
The element-by-element result of the operator+ is the
valarray: ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
```

## <a name="operator"></a><a name="op_add_eq"></a> 运算符 + =

将指定 valarray 的元素或元素类型的值与操作数 valarray 进行点加。

```cpp
valarray<Type>& operator+=(const valarray<Type>& right);

valarray<Type>& operator+=(const Type& right);
```

### <a name="parameters"></a>parameters

*然后*\
valarray 或值与操作数 valarray 的 valarray 或值相同的元素类型，用于对操作数 valarray 进行点加。

### <a name="return-value"></a>返回值

一个 valarray，其元素是操作数 valarray 和 *right* 的按元素的和。

### <a name="example"></a>示例

```cpp
// valarray_op_eadd.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial  right valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL += vaR;
   cout << "The element-by-element result of "
        << "the sum is the"
        << endl << "valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the sum is the
valarray: ( 2 0 4 2 6 4 8 6 ).
```

## <a name="operator-"></a><a name="operator-"></a> 操作员

一个一元运算符，该运算符将 valarray 中的所有元素相减。

```cpp
valarray<Type> operator-() const;
```

### <a name="return-value"></a>返回值

一个 valarray，它的元素是操作数数列的元素的差。

### <a name="example"></a>示例

```cpp
// valarray_op_eminus.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 );
   valarray<int> vaMINUS ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;

   cout << "The initial valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   vaMINUS = -vaL;
   cout << "The element-by-element result of "
        << "the operator+ is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaMINUS [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
The element-by-element result of the operator+ is the
valarray: ( 0 0 2 -2 4 -4 6 -6 8 -8 ).
```

## <a name="operator-"></a><a name="operator-_eq"></a> operator-=

将指定 valarray 的元素或元素类型的值与操作数 valarray 进行点减。

```cpp
valarray<Type>& operator-=(const valarray<Type>& right);

valarray<Type>& operator-=(const Type& right);
```

### <a name="parameters"></a>parameters

*然后*\
valarray 或值与操作数 valarray 的 valarray 或值相同的元素类型，用于对操作数 valarray 进行点减。

### <a name="return-value"></a>返回值

一个 valarray，其元素是操作数 valarray 和 *right* 的按元素的差。

### <a name="example"></a>示例

```cpp
// valarray_op_esub.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  10;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial  right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL -= vaR;
   cout << "The element-by-element result of "
        << "the difference is the"
        << endl << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is: ( 10 0 10 0 10 0 10 0 ).
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the difference is the
valarray: ( 10 -1 8 -3 6 -5 4 -7 ).
```

## <a name="operator"></a><a name="op_div_eq"></a> operator/=

将操作数 valarray 与指定 valarray 的元素或元素类型的值进行点除。

```cpp
valarray<Type>& operator/=(const valarray<Type>& right);

valarray<Type>& operator/=(const Type& right);
```

### <a name="parameters"></a>parameters

*然后*\
valarray 或值与操作数 valarray 的 valarray 或值相同的元素类型，用于对操作数 valarray 进行点除。

### <a name="return-value"></a>返回值

一个 valarray，其元素是操作数 valarray 的面向 *元素的商。*

### <a name="example"></a>示例

```cpp
// valarray_op_ediv.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<double> vaL ( 6 ), vaR ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  100;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -100;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  2*i;

   cout << "The initial valarray is: ( ";
      for (i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL /= vaR;
   cout << "The element-by-element result of "
        << "the quotient is the"
        << endl << "valarray: ( ";
      for (i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial valarray is: ( 100 -100 100 -100 100 -100 ).
The initial Right valarray is: ( 0 2 4 6 8 10 ).
The element-by-element result of the quotient is the
valarray: ( inf -50 25 -16.6667 12.5 -10 ).
```

## <a name="operator"></a><a name="op_eq"></a> operator =

将元素分配给 valarray，其值可以直接指定，也可以作为一些其他 valarray 的一部分指定，或由 slice_array、gslice_array、mask_array 或 indirect_array 指定。

```cpp
valarray<Type>& operator=(const valarray<Type>& right);

valarray<Type>& operator=(valarray<Type>&& right);

valarray<Type>& operator=(const Type& val);

valarray<Type>& operator=(const slice_array<Type>& _Slicearray);

valarray<Type>& operator=(const gslice_array<Type>& _Gslicearray);

valarray<Type>& operator=(const mask_array<Type>& _Maskarray);

valarray<Type>& operator=(const indirect_array<Type>& _Indarray);
```

### <a name="parameters"></a>parameters

*然后*\
要复制到操作数 valarray 中的 valarray。

*初始值*\
要分配给操作数 valarray 的元素的值。

*_Slicearray*\
要复制到操作数 valarray 中的 slice_array。

*_Gslicearray*\
要复制到操作数 valarray 中的 gslice_array。

*_Maskarray*\
要复制到操作数 valarray 中的 mask_array。

*_Indarray*\
要复制到操作数 valarray 中的 indirect_array。

### <a name="return-value"></a>返回值

第一个成员运算符将受控序列替换为由 *right* 控制的序列副本。

第二个成员运算符与第一个成员运算符相同，但前者具有[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

第三个成员运算符使用 *val* 的副本替换受控序列的每个元素。

其余成员运算符将替换其参数选择的受控序列的元素，这些参数仅由 [operator[]](#op_at) 生成。

如果替换受控序列中的成员值取决于最初的受控序列中的成员，则结果不可确定。

### <a name="remarks"></a>备注

如果受控序列的长度发生更改，则结果通常不可确定。 但是在此实现中，结果仅仅是使受控序列中元素的任何指针或引用均失效。

### <a name="example"></a>示例

```cpp
// valarray_op_assign.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 10 ), vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 1 )
      va [ i ] = i;
   for ( i = 0 ; i < 10 ; i+=1 )
      vaR [ i ] = 10 -  i;

   cout << "The operand valarray va is:";
   for ( i = 0 ; i < 10 ; i++ )
      cout << " " << va [ i ];
   cout << endl;

   cout << "The operand valarray vaR is:";
      for ( i = 0 ; i < 10 ; i++ )
         cout << " " << vaR [ i ];
   cout << endl;

   // Assigning vaR to va with the first member functon
   va = vaR;
   cout << "The reassigned valarray va is:";
   for ( i = 0 ; i < 10 ; i++ )
      cout << " " << va [ i ];
   cout << endl;

   // Assigning elements of value 10 to va
   // with the second member functon
   va = 10;
   cout << "The reassigned valarray va is:";
      for ( i = 0 ; i < 10 ; i++ )
         cout << " " << va [ i ];
   cout << endl;
}
```

```Output
The operand valarray va is: 0 1 2 3 4 5 6 7 8 9
The operand valarray vaR is: 10 9 8 7 6 5 4 3 2 1
The reassigned valarray va is: 10 9 8 7 6 5 4 3 2 1
The reassigned valarray va is: 10 10 10 10 10 10 10 10 10 10

```

## <a name="operator"></a><a name="op_at"></a> operator[]

返回对指定索引或指定子集处的元素或其值的引用。

```cpp
Type& operator[](size_t _Off);

slice_array<Type> operator[](slice _Slicearray);

gslice_array<Type> operator[](const gslice& _Gslicearray);

mask_array<Type> operator[](const valarray<bool>& _Boolarray);

indirect_array<Type> operator[](const valarray<size_t>& _Indarray);

Type operator[](size_t _Off) const;

valarray<Type> operator[](slice _Slice) const;

valarray<Type> operator[](const gslice& _Gslicearray) const;

valarray<Type> operator[](const valarray<bool>& _Boolarray) const;

valarray<Type> operator[](const valarray<size_t>& _Indarray) const;
```

### <a name="parameters"></a>parameters

*_Off*\
要对其进行赋值的元素的索引。

*_Slicearray*\
一个 valarray 的 slice_array，它指定要选择或返回到新 valarray 的子集。

*_Gslicearray*\
一个 valarray 的 gslice_array，它指定要选择或返回到新 valarray 的子集。

*_Boolarray*\
一个 valarray 的 bool_array，它指定要选择或返回到新 valarray 的子集。

*_Indarray*\
一个 valarray 的 indirect_array，它指定要选择或返回到新 valarray 的子集。

### <a name="return-value"></a>返回值

对指定索引或指定子集处的元素或其值的引用。

### <a name="remarks"></a>备注

重载成员运算符以提供多种方法来选择元素<strong> \* 序列，从此类控制。</strong> 五个成员运算符中的第一组将配合 [operator=](#op_eq)（以及其他赋值运算符）的各种重载进行工作，从而允许受控序列的选择性替换（切片）。 所选的元素必须存在。

当使用定义为 1 或 2 的 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 进行编译时，如果试图访问 valarray 的边界之外的元素，将发生运行时错误。  有关更多信息，请参见 [Checked Iterators](../standard-library/checked-iterators.md) 。

### <a name="example"></a>示例

有关如何声明和使用此运算符的示例，请参阅 [slice::slice](../standard-library/slice-class.md#slice) 和 [gslice::gslice](../standard-library/gslice-class.md#gslice) 的示例。

## <a name="operator"></a><a name="op_xor_eq"></a> operator ^ =

获取数组与指定 valarray 或元素类型的值进行的点排除逻辑或运算符 (**XOR**)。

```cpp
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```

### <a name="parameters"></a>parameters

*然后*\
valarray 或值与操作数 valarray 的 valarray 或值相同的元素类型，用于通过排他逻辑 **XOR** 与操作数 valarray 进行点算合并。

### <a name="return-value"></a>返回值

一个 valarray，其元素是操作数 valarray 和 *right* 的按元素、排他逻辑 **XOR** 。

### <a name="remarks"></a>备注

排他逻辑 or （称为 **XOR**）具有以下语义：给定元素 *e* 1 和 *e* 2; 如果只有一个元素为 true，则 *e* 1 **XOR** *e* 2 为 true; 如果两个元素都为 true，则为 **`true`** ; 如果 **`false`** 这两个元素均为 true，则为。

### <a name="example"></a>示例

```cpp
// valarray_op_exor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
    using namespace std;
    int i;

    valarray<int> vaL ( 10 ), vaR ( 10 );
    for ( i = 0 ; i < 10 ; i += 2 )
        vaL [ i ] =  1;
    for ( i = 1 ; i < 10 ; i += 2 )
        vaL [ i ] =  0;
    for ( i = 0 ; i < 10 ; i += 3 )
        vaR [ i ] =  i;
    for ( i = 1 ; i < 10 ; i += 3 )
        vaR [ i ] =  i-1;
    for ( i = 2 ; i < 10 ; i += 3 )
        vaR [ i ] =  i-1;

    cout << "The initial operand valarray is:  ( ";
        for (i = 0 ; i < 10 ; i++ )
            cout << vaL [ i ] << " ";
    cout << ")." << endl;

    cout << "The  right valarray is: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaR [ i ] << " ";
    cout << ")." << endl;

    vaL ^= vaR;
    cout << "The element-by-element result of "
        << "the bitwise XOR operator^= is the"
        << endl << "valarray: ( ";
        for (i = 0 ; i < 10 ; i++ )
            cout << vaL [ i ] << " ";
    cout << ")." << endl;
}
```

```Output
The initial operand valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The  right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise XOR operator^= is the
valarray: ( 1 0 0 3 2 4 7 6 6 9 ).
```

## <a name="operator124"></a><a name="op_or_eq"></a> 运算符&#124;=

获取数组中元素的按位 `OR`，该数组具有指定 valarray 中的对应元素或具有元素类型的值。

```cpp
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```

### <a name="parameters"></a>parameters

*然后*\
valarray 或值与操作数 valarray 的 valarray 或值相同的元素类型，用于通过按位 `OR` 与操作数 valarray 进行点算合并。

### <a name="return-value"></a>返回值

一个 valarray，其元素为 `OR` 操作数 valarray by *right* 的按位。

### <a name="remarks"></a>备注

按位运算仅可用于操作和数据类型中的位和 **`char`** **`int`** 变体，不能用于 **`float`** 、 **`double`** 、 **longdouble**、 **`void`** 、 **`bool`** 或其他更复杂的数据类型。

按位 `OR` 具有与逻辑 `OR` 相同的事实表，但是按位 OR 适用于单个位级别上的数据类型。 给定位 *b* 1 和 *b* 2，  `OR` 如果至少有一个位为 true，则 b 1 *b* 2 **`true`** ; **`false`** 如果两个位都为 false，则为。

### <a name="example"></a>示例

```cpp
// valarray_class_op_bitor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;

   cout << "The initial operand valarray is:"
        << endl << "( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The  right valarray is:"
        << endl << "( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL |= vaR;
   cout << "The element-by-element result of "
        << "the logical OR"
        << endl << "operator|= is the valarray:"
        << endl << "( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial operand valarray is:
( 1 0 1 0 1 0 1 0 1 0 ).
The  right valarray is:
( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the logical OR
operator|= is the valarray:
( 1 0 1 3 3 4 7 6 7 9 ).
```

## <a name="operator"></a><a name="op_dtor"></a> 运算符 ~

一个一元运算符，该运算符获取 `NOT` valarray 中每个元素的按位值。

```cpp
valarray<Type> operator~() const;
```

### <a name="return-value"></a>返回值

布尔值的 valarray，这些布尔值是 `NOT` 操作数 valarray 的元素值的按位。

### <a name="remarks"></a>备注

按位运算仅可用于操作和数据类型中的位和 **`char`** **`int`** 变体，不能用于 **`float`** 、 **`double`** 、 **longdouble**、 **`void`** **`bool`** 或其他更复杂的数据类型。

按位 `NOT` 具有与逻辑 `NOT` 相同的事实表，但是按位 OR 适用于单个位级别上的数据类型。 假设有位 b，如果 b 为 false，则 ~ *b* 为 true；如果 b 为 true，则为 false。 逻辑 **NOT**[operator!](#op_not) 适用于元素级别，将所有非零值计算为 **`true`** ，结果为布尔值的 valarray。 与此相反，按位 "与" `NOToperator~` 运算可能会产生0或1以外的值的 valarray，具体取决于按位运算的结果。

### <a name="example"></a>示例

```cpp
// valarray_op_bitnot.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
    using namespace std;
    int i;

    valarray<unsigned short int> vaL1 ( 10 );
    valarray<unsigned short int> vaNOT1 ( 10 );
    for ( i = 0 ; i < 10 ; i += 2 )
        vaL1 [ i ] =  i;
    for ( i = 1 ; i < 10 ; i += 2 )
        vaL1 [ i ] =  5*i;

    cout << "The initial valarray <unsigned short int> is:  ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaL1 [ i ] << " ";
    cout << ")." << endl;

    vaNOT1 = ~vaL1;
    cout << "The element-by-element result of "
        << "the bitwise NOT operator~ is the"
        << endl << "valarray: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaNOT1 [ i ] << " ";
    cout << ")." << endl << endl;

    valarray<int> vaL2 ( 10 );
    valarray<int> vaNOT2 ( 10 );
    for ( i = 0 ; i < 10 ; i += 2 )
        vaL2 [ i ] =  i;
    for ( i = 1 ; i < 10 ; i += 2 )
        vaL2 [ i ] =  -2 * i;

    cout << "The initial valarray <int> is:  ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaL2 [ i ] << " ";
    cout << ")." << endl;

    vaNOT2 = ~vaL2;
    cout << "The element-by-element result of "
        << "the bitwise NOT operator~ is the"
        << endl << "valarray: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaNOT2 [ i ] << " ";
    cout << ")." << endl;

    // The negative numbers are represented using
    // the two's complement approach, so adding one
    // to the flipped bits returns the negative elements
    vaNOT2 = vaNOT2 + 1;
    cout << "The element-by-element result of "
        << "adding one"
        << endl << "is the negative of the "
        << "original elements the"
        << endl << "valarray: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << vaNOT2 [ i ] << " ";
    cout << ")." << endl;
}
```

```Output
The initial valarray <unsigned short int> is:  ( 0 5 2 15 4 25 6 35 8 45 ).
The element-by-element result of the bitwise NOT operator~ is the
valarray: ( 65535 65530 65533 65520 65531 65510 65529 65500 65527 65490 ).

The initial valarray <int> is:  ( 0 -2 2 -6 4 -10 6 -14 8 -18 ).
The element-by-element result of the bitwise NOT operator~ is the
valarray: ( -1 1 -3 5 -5 9 -7 13 -9 17 ).
The element-by-element result of adding one
is the negative of the original elements the
valarray: ( 0 2 -2 6 -4 10 -6 14 -8 18 ).
```

## <a name="resize"></a><a name="resize"></a> 调节

将 valarray 中的元素数更改为指定数量。

```cpp
void resize(
    size_t _Newsize);

void resize(
    size_t _Newsize,
    const Type val);
```

### <a name="parameters"></a>parameters

*_Newsize*\
调整大小后的 valarray 中的元素数。

*初始值*\
要提供给调整大小后的 valarray 的元素的值。

### <a name="remarks"></a>备注

第一个成员函数使用其默认构造函数初始化元素。

受控序列中元素的任何指针或引用都会失效。

### <a name="example"></a>示例

下面的示例演示如何使用 valarray::resize 成员函数。

```cpp
// valarray_resize.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;
    size_t size1, sizeNew;

    valarray<int> va1(10);
    for (i = 0; i < 10; i+=1)
        va1[i] = i;

    cout << "The valarray contains ( ";
        for (i = 0; i < 10; i++)
            cout << va1[i] << " ";
    cout << ")." << endl;

    size1 = va1.size();
    cout << "The number of elements in the valarray is: "
         << size1  << "." <<endl << endl;

    va1.resize(15, 10);

    cout << "The valarray contains ( ";
        for (i = 0; i < 15; i++)
            cout << va1[i] << " ";
    cout << ")." << endl;
    sizeNew = va1.size();
    cout << "The number of elements in the resized valarray is: "
         << sizeNew  << "." <<endl << endl;
}
```

```Output
The valarray contains ( 0 1 2 3 4 5 6 7 8 9 ).
The number of elements in the valarray is: 10.

The valarray contains ( 10 10 10 10 10 10 10 10 10 10 10 10 10 10 10 ).
The number of elements in the resized valarray is: 15.
```

## <a name="shift"></a><a name="shift"></a> 格

将 valarray 中的所有元素按指定位数移动。

```cpp
valarray<Type> shift(int count) const;
```

### <a name="parameters"></a>parameters

*计*\
要向前移动元素的位数。

### <a name="return-value"></a>返回值

新的 valarray，其中所有元素都已移动到 valarray 前面的位置，相对于它们在操作数 valarray 中 *的位置。*

### <a name="remarks"></a>备注

如果正值为 *count* ，则将元素向左偏移 *数* 个位置，并使用零填充。

如果 *负值为负值* ，则将元素右移 *count* 个位置，并使用零填充。

### <a name="example"></a>示例

```cpp
// valarray_shift.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va1 ( 10 ), va2 ( 10 );
   for ( i = 0 ; i < 10 ; i += 1 )
      va1 [ i ] =  i;
   for ( i = 0 ; i < 10 ; i += 1 )
      va2 [ i ] = 10 -  i;

   cout << "The operand valarray va1(10) is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va1 [ i ] << " ";
   cout << ")." << endl;

   // A positive parameter shifts elements left
   va1 = va1.shift ( 4 );
   cout << "The shifted valarray va1 is: va1.shift (4) = ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va1 [ i ] << " ";
   cout << ")." << endl;

   cout << "The operand valarray va2(10) is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va2 [ i ] << " ";
   cout << ")." << endl;

   // A negative parameter shifts elements right
   va2 = va2.shift ( - 4 );
   cout << "The shifted valarray va2 is: va2.shift (-4) = ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va2 [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The shifted valarray va1 is: va1.shift (4) = ( 4 5 6 7 8 9 0 0 0 0 ).
The operand valarray va2(10) is: ( 10 9 8 7 6 5 4 3 2 1 ).
The shifted valarray va2 is: va2.shift (-4) = ( 0 0 0 0 10 9 8 7 6 5 ).
```

## <a name="size"></a><a name="size"></a> 规格

返回 valarray 中的元素数。

```cpp
size_t size() const;
```

### <a name="return-value"></a>返回值

操作数 valarray 中的元素数。

### <a name="example"></a>示例

下面的示例演示如何使用 valarray::size 成员函数。

```cpp
// valarray_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;
    size_t size1, size2;

    valarray<int> va1(10), va2(12);
    for (i = 0; i < 10; i += 1)
        va1[i] =  i;
    for (i = 0; i < 10; i += 1)
        va2[i] =  i;

    cout << "The operand valarray va1(10) is: ( ";
        for (i = 0; i < 10; i++)
            cout << va1[i] << " ";
    cout << ")." << endl;

    size1 = va1.size();
    cout << "The number of elements in the valarray va1 is: va1.size = "
         << size1  << "." <<endl << endl;

    cout << "The operand valarray va2(12) is: ( ";
        for (i = 0; i < 10; i++)
            cout << va2[i] << " ";
    cout << ")." << endl;

    size2 = va2.size();
    cout << "The number of elements in the valarray va2 is: va2.size = "
         << size2  << "." << endl << endl;

    // Initializing two more elements to va2
    va2[10] = 10;
    va2[11] = 11;
    cout << "After initializing two more elements,\n"
         << "the operand valarray va2(12) is now: ( ";
        for (i = 0; i < 12; i++)
            cout << va2[i] << " ";
    cout << ")." << endl;
    cout << "The number of elements in the valarray va2 is still: "
         << size2  << "." << endl;
}
```

```Output
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The number of elements in the valarray va1 is: va1.size = 10.

The operand valarray va2(12) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The number of elements in the valarray va2 is: va2.size = 12.

After initializing two more elements,
the operand valarray va2(12) is now: ( 0 1 2 3 4 5 6 7 8 9 10 11 ).
The number of elements in the valarray va2 is still: 12.
```

## <a name="sum"></a><a name="sum"></a> 长度

确定长度不为零的 valarray 中的所有元素的总和。

```cpp
Type sum() const;
```

### <a name="return-value"></a>返回值

操作数 valarray 的元素总和。

### <a name="remarks"></a>备注

如果长度大于1，则成员函数将值添加到 sum，方法是在类的一 `operator+=` 对元素之间应用 `Type` ，因此需要为类型的元素提供运算符 `Type` 。

### <a name="example"></a>示例

```cpp
// valarray_sum.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
    using namespace std;
    int i;
    int sumva = 0;

    valarray<int> va ( 10 );
    for ( i = 0 ; i < 10 ; i+=1 )
        va [ i ] =  i;

    cout << "The operand valarray va (10) is: ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << va [ i ] << " ";
    cout << ")." << endl;

    sumva = va.sum ( );
    cout << "The sum of elements in the valarray is: "
        << sumva  << "." <<endl;
}
```

```Output
The operand valarray va (10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The sum of elements in the valarray is: 45.
```

## <a name="swap"></a><a name="swap"></a> 购

交换两个 `valarray` 的元素。

```cpp
void swap(valarray& right);
```

### <a name="parameters"></a>parameters

*然后*\
一个 `valarray`，提供要交换的元素。

### <a name="remarks"></a>备注

成员函数交换和右之间的受控 **`*this`** 序列。 它在固定时间内执行此操作，它不引发任何异常，不使任何引用、指针或指定两个受控序列中的元素的迭代器失效。

## <a name="valarray"></a><a name="valarray"></a> valarray

构造特定大小的数值数组、带特定值的元素的数值数组、作为另一个数值数组的副本或另一个数值数组的子集的数值数组。

```cpp
valarray();

explicit valarray(
    size_t Count);

valarray(
    const Type& Val,
    size_t Count);

valarray(
    const Type* Ptr,
    size_t Count);

valarray(
    const valarray<Type>& Right);

valarray(
    const slice_array<Type>& SliceArray);

valarray(
    const gslice_array<Type>& GsliceArray);

valarray(
    const mask_array<Type>& MaskArray);

valarray(
    const indirect_array<Type>& IndArray);

valarray(
    valarray<Type>&& Right);

valarray(
    initializer_list<Type> IList);
```

### <a name="parameters"></a>parameters

*计*\
数值数组要包含的元素的数目。

*初始值*\
要用于初始化数值数组中的元素的值。

*Ptr*\
指向要用于初始化数值数组中的元素的值的指针。

*然后*\
用于初始化新数值数组的现有数值数组。

*SliceArray*\
其元素值要用于初始化要构造的数值数组的元素的 slice_array。

*GsliceArray*\
其元素值要用于初始化要构造的数值数组的元素的 gslice_array。

*MaskArray*\
其元素值要用于初始化要构造的数值数组的元素的 mask_array。

*IndArray*\
其元素值要用于初始化要构造的数值数组的元素的 indirect_array。

*IList*\
包含要复制的元素的 initializer_list。

### <a name="remarks"></a>备注

第一个（默认）构造函数将对象初始化为空数组。 接下来的三个构造函数将对象初始化为 *Count* 元素数组，如下所示：

- 对于显式 `valarray(size_t Count)`，使用默认构造函数初始化每个元素。

- 对于 `valarray(const Type& Val, Count)` ，每个元素都是用 *Val* 初始化的。

- 对于 `valarray(const Type* Ptr, Count)`，使用 `Ptr`[ `I`] 初始化位置 `I` 处的元素。

其余每个构造函数将对象初始化为 \<Type> 由参数中指定的子集确定的 valarray 对象。

最后一个构造函数与倒数第二个构造函数相同，但前者具有[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

### <a name="example"></a>示例

```cpp
// valarray_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;

    // The second member function
    valarray<int> va(10);
    for (auto i : va){
        va[i] = 2 * (i + 1);
    }

    cout << "The operand valarray va is:\n(";
    for (auto i : va) {
        cout << " " << va[i];
    }
    cout << " )" << endl;

    slice Slice(2, 4, 3);

    // The fifth member function
    valarray<int> vaSlice = va[Slice];

    cout << "The new valarray initialized from the slice is vaSlice =\n"
        << "va[slice( 2, 4, 3)] = (";
    for (int i = 0; i < 3; i++) {
        cout << " " << vaSlice[i];
    }
    cout << " )" << endl;

    valarray<int> va2{{ 1, 2, 3, 4 }};
    for (auto& v : va2) {
        cout << v << " ";
    }
    cout << endl;
}
```

```Output
The operand valarray va is:
( 0 2 2 2 2 2 2 2 2 2 )
The new valarray initialized from the slice is vaSlice =
va[slice( 2, 4, 3)] = ( 0 0 0 )
1 2 3 4
```

## <a name="value_type"></a><a name="value_type"></a> value_type

一种类型，表示存储在 valarray 中的元素类型。

```cpp
typedef Type value_type;
```

### <a name="remarks"></a>备注

类型是模板参数 `Type` 的同义词。

### <a name="example"></a>示例

```cpp
// valarray_value_type.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
    using namespace std;
    int i;
    valarray<int> va ( 10 );
    for ( i = 0 ; i < 10 ; i += 2 )
        va [ i ] =  i;
    for ( i = 1 ; i < 10 ; i += 2 )
        va [ i ] =  -1;

    cout << "The initial operand valarray is:  ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << va [ i ] << " ";
    cout << ")." << endl;

    // value_type declaration and initialization:
    valarray<int>::value_type Right = 10;

    cout << "The decalared value_type Right is: "
            << Right << endl;
    va *= Right;
    cout << "The resulting valarray is:  ( ";
        for ( i = 0 ; i < 10 ; i++ )
            cout << va [ i ] << " ";
    cout << ")." << endl;
}
```

```Output
The initial operand valarray is:  ( 0 -1 2 -1 4 -1 6 -1 8 -1 ).
The decalared value_type Right is: 10
The resulting valarray is:  ( 0 -10 20 -10 40 -10 60 -10 80 -10 ).
```

## <a name="see-also"></a>请参阅

[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
