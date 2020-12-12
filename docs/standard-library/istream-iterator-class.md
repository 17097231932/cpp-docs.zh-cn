---
description: 了解详细信息： istream_iterator 类
title: istream_iterator 类
ms.date: 11/04/2016
f1_keywords:
- iterator/std::istream_iterator
- iterator/std::istream_iterator::char_type
- iterator/std::istream_iterator::istream_type
- iterator/std::istream_iterator::traits_type
helpviewer_keywords:
- std::istream_iterator [C++]
- std::istream_iterator [C++], char_type
- std::istream_iterator [C++], istream_type
- std::istream_iterator [C++], traits_type
ms.assetid: fb52a8cd-7f71-48d1-b73e-4b064e2a8d16
ms.openlocfilehash: 7247e96c68f1adcc145519fc1cca6b3401302854
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277903"
---
# <a name="istream_iterator-class"></a>istream_iterator 类

描述一个输入迭代器对象。 它从输入流中提取 `Type` 类的对象，并通过其存储的、指向 `basic_istream`< `CharType`, `Traits`> 的 `pointer` 类型对象访问此输入流。

## <a name="syntax"></a>语法

```cpp
template <class Type, class CharType = char, class Traits = char_traits<CharType>, class Distance = ptrdiff_t,>
class istream_iterator
: public iterator<
    input_iterator_tag, Type, Distance,
    const Type *,
    const Type&>;
```

### <a name="parameters"></a>parameters

*类别*\
要从输入流中提取的对象的类型。

*CharType*\
表示 `istream_iterator` 字符类型的类型。 此参数是可选的，默认值为 **`char`** 。

*特征*\
表示 `istream_iterator` 字符类型的类型。 此自变量是可选自变量，默认值为 `char_traits`< `CharType`>。

*长途*\
表示 `istream_iterator` 差异类型的带符号的整数类型。 此参数为可选参数，默认值为 `ptrdiff_t`。

构造或递增带有非 null 存储指针的 istream_iterator 类对象后，此对象将尝试从关联的输入流提取和存储 `Type` 类型的对象。 如果提取失败，对象将使用 null 指针有效替换存储指针，从而设置序列末尾指示符。

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[istream_iterator](#istream_iterator)|构造一个流结尾迭代器作为默认的 `istream_iterator`，或作为一个 `istream_iterator`，以便初始化为它开始读取的迭代器流类型。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[char_type](#char_type)|为 `istream_iterator` 的字符类型提供的类型。|
|[istream_type](#istream_type)|为 `istream_iterator` 的流类型提供的类型。|
|[traits_type](#traits_type)|为 `istream_iterator` 的字符特征类型提供的类型。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[操作员](#op_star)|此解引用运算符返回由 `Type` 定址的、`istream_iterator` 类型的存储对象。|
|[operator->](#op_arrow)|返回成员的值（如果有）。|
|[operator + +](#op_add_add)|从输入流提取增量对象，或在递增对象之前复制对象并返回副本。|

## <a name="requirements"></a>要求

**标头：**\<iterator>

**命名空间:** std

## <a name="istream_iteratorchar_type"></a><a name="char_type"></a> istream_iterator：： char_type

为 `istream_iterator` 的字符类型提供的类型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>备注

类型是模板参数 `Chartype` 的同义词。

### <a name="example"></a>示例

```cpp
// istream_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef istream_iterator<int>::char_type CHT1;
   typedef istream_iterator<int>::traits_type CHTR1;

   // Standard iterator interface for reading
   // elements from the input stream:
   cout << "Enter integers separated by spaces & then\n"
        << " any character ( try example: '2 4 f' ): ";

   // istream_iterator for reading int stream
   istream_iterator<int, CHT1, CHTR1> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int, CHT1, CHTR1> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="istream_iteratoristream_iterator"></a><a name="istream_iterator"></a> istream_iterator：： istream_iterator

构造一个流结尾迭代器作为默认的 `istream_iterator`，或作为一个 `istream_iterator`，以便初始化为它开始读取的迭代器流类型。

```cpp
istream_iterator();

istream_iterator(istream_type& _Istr);
```

### <a name="parameters"></a>parameters

*_Istr*\
要读取以用于初始化 `istream_iterator` 的输入流。

### <a name="remarks"></a>备注

第一个构造函数通过空指针初始化输入流指针，并创建流末尾迭代器。 第二个构造函数使用 *&_Istr* 初始化输入流指针，然后尝试提取并存储类型的对象 `Type` 。

流末尾迭代器可用于测试 `istream_iterator` 是否已达到流末尾。

### <a name="example"></a>示例

```cpp
// istream_iterator_istream_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   // Used in conjunction with copy algorithm
   // to put elements into a vector read from cin
   vector<int> vec ( 4 );
   vector <int>::iterator Iter;

   cout << "Enter 4 integers separated by spaces & then\n"
        << " a character ( try example: '2 4 6 8 a' ): ";
   istream_iterator<int> intvecRead ( cin );

   // Default constructor will test equal to end of stream
   // for delimiting source range of vecor
   copy ( intvecRead , istream_iterator<int>( ) , vec.begin ( ) );
   cin.clear ( );

   cout << "vec = ";
   for ( Iter = vec.begin( ) ; Iter != vec.end( ) ; Iter++ )
      cout << *Iter << " "; cout << endl;
}
```

## <a name="istream_iteratoristream_type"></a><a name="istream_type"></a> istream_iterator：： istream_type

为 `istream_iterator` 的流类型提供的类型。

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>备注

类型是的同义词 `basic_istream` \< **CharType**, **Traits**> 。

### <a name="example"></a>示例

有关如何声明和使用 `istream_type` 的示例，请参阅 [istream_iterator](#istream_iterator)。

## <a name="istream_iteratoroperator"></a><a name="op_star"></a> istream_iterator：： operator *

此解引用运算符返回由 `Type` 定址的、`istream_iterator` 类型的存储对象。

```cpp
const Type& operator*() const;
```

### <a name="return-value"></a>返回值

类型的存储对象 `Type` 。

### <a name="example"></a>示例

```cpp
// istream_iterator_operator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Enter integers separated by spaces & then\n"
        << " a character ( try example: '2 4 6 8 a' ): ";

   // istream_iterator from stream cin
   istream_iterator<int> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="istream_iteratoroperator-gt"></a><a name="op_arrow"></a> istream_iterator：： operator-&gt;

返回成员的值（如果有）。

```cpp
const Type* operator->() const;
```

### <a name="return-value"></a>返回值

成员的值（如有）。

### <a name="remarks"></a>备注

`i->m` 等效于 `(*i).m`

运算符返回 `&*this`。

### <a name="example"></a>示例

```cpp
// istream_iterator_operator_vm.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>
#include <complex>

using namespace std;

int main( )
{
   cout << "Enter complex numbers separated by spaces & then\n"
        << " a character pair ( try example: '(1,2) (3,4) (a,b)' ): ";

   // istream_iterator from stream cin
   istream_iterator< complex<double> > intRead ( cin );

   // End-of-stream iterator
   istream_iterator<complex<double> > EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading the real part: " << intRead ->real( ) << endl;
      cout << "Reading the imaginary part: " << intRead ->imag( ) << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="istream_iteratoroperator"></a><a name="op_add_add"></a> istream_iterator：： operator + +

从输入流提取增量对象，或在递增对象之前复制对象并返回副本。

```cpp
istream_iterator<Type, CharType, Traits, Distance>& operator++();

istream_iterator<Type, CharType, Traits, Distance> operator++(int);
```

### <a name="return-value"></a>返回值

第一个成员运算符返回对从输入流中提取的类型的递增对象的引用 `Type` ，第二个成员函数返回该对象的副本。

### <a name="example"></a>示例

```cpp
// istream_iterator_operator_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Enter integers separated by spaces & then\n"
        << " a character ( try example: '2 4 6 8 a' ): ";

   // istream_iterator from stream cin
   istream_iterator<int> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="istream_iteratortraits_type"></a><a name="traits_type"></a> istream_iterator：： traits_type

为 `istream_iterator` 的字符特征类型提供的类型。

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>备注

该类型是模板参数 *Traits* 的同义词。

### <a name="example"></a>示例

```cpp
// istream_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   typedef istream_iterator<int>::char_type CHT1;
   typedef istream_iterator<int>::traits_type CHTR1;

   // Standard iterator interface for reading
   // elements from the input stream:
   cout << "Enter integers separated by spaces & then\n"
        << " any character ( try example: '10 20 a' ): ";

   // istream_iterator for reading int stream
   istream_iterator<int, CHT1, CHTR1> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int, CHT1, CHTR1> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="see-also"></a>请参阅

[input_iterator_tag 结构](../standard-library/input-iterator-tag-struct.md)\
[iterator 结构](../standard-library/iterator-struct.md)\
[\<iterator>](../standard-library/iterator.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 标准库参考](../standard-library/cpp-standard-library-reference.md)
