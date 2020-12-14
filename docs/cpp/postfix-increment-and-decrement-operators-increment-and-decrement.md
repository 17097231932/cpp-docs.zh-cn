---
description: 了解详细信息：后缀增量和减量运算符： + + 和--
title: 后缀增量和减量运算符：++ 和 --
ms.date: 11/04/2016
f1_keywords:
- --
- ++
helpviewer_keywords:
- increment operators [C++], syntax
- member-selection operators [C++]
- -- operator [C++], postfix decrement operators
- postfix operators [C++]
- ++ operator [C++], postfix increment operators
- decrement operators [C++], syntax
- operators [C++], postfix
- decrement operators [C++]
ms.assetid: 0204d5c8-51b0-4108-b8a1-074c5754d89c
ms.openlocfilehash: 56f955fc4c8b5508c4b2c4e03c37e89f9d2d8bc0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258507"
---
# <a name="postfix-increment-and-decrement-operators--and---"></a>后缀增量和减量运算符：++ 和 --

## <a name="syntax"></a>语法

```
postfix-expression ++
postfix-expression --
```

## <a name="remarks"></a>备注

C++ 提供了前缀和后缀递增和递减运算符；本节仅介绍后缀递增和递减运算符。  (有关详细信息，请参阅 [前缀增量和减量运算符](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)。 ) 两者之间的差异在于，在后缀表示法中，运算符出现在 *后缀表达式* 之后，而在前缀表示法中，运算符出现在 *expression 之前。* 以下示例显示了一个后缀递增运算符：

```cpp
i++;
```

 () 应用后缀递增运算符的效果 **++** 是操作数的值增加一个适当类型的单位。 同样，将后缀减量运算符应用于)  (的效果 **--** 是操作数的值减小了一个适当类型的单位。

需要注意的是，后缀递增或递减表达式的计算结果为在应用各自运算符 *之前* 的表达式的值。 递增或递减运算在计算操作数 *之后* 发生。 仅当在较大的表达式的上下文中发生后缀递增或递减运算时才会出现此问题。

当后缀运算符应用于函数参数时，在参数的值传递给函数之前，不能保证该值是递增还是递减。  有关详细信息，请参阅 C++ 标准中的 1.9.17 节。

将后缀递增运算符应用到类型的对象数组的指针 **`long`** 实际上会将四个添加到指针的内部表示形式。 此行为会导致指针（以前引用数组的第 *n* 个元素）引用第 (*n*+ 1) 个元素。

后缀递增和后缀减量运算符的操作数必须是可修改的， (不 **`const`**) 算术类型或指针类型的值。 结果的类型与 *后缀表达式* 的类型相同，但它不再是左值。

**Visual Studio 2017 版本15.3 及更高版本** (随 [/std 提供： c + + 17](../build/reference/std-specify-language-standard-version.md)) ：后缀递增或递减运算符的操作数的类型不能为 **`bool`** 。

以下代码演示了后缀递增运算符：

```cpp
// expre_Postfix_Increment_and_Decrement_Operators.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main() {
   int i = 10;
   cout << i++ << endl;
   cout << i << endl;
}
```

不支持对枚举类型执行后递增和后递减操作：

```cpp
enum Compass { North, South, East, West );
Compass myCompass;
for( myCompass = North; myCompass != West; myCompass++ ) // Error
```

## <a name="see-also"></a>请参阅

[后缀表达式](../cpp/postfix-expressions.md)<br/>
[C++ 内置运算符、优先级和关联性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 后缀递增和递减运算符](../c-language/c-postfix-increment-and-decrement-operators.md)
