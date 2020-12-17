---
description: 详细了解：C 按位运算符
title: C 按位运算符
ms.date: 01/29/2018
helpviewer_keywords:
- '| operator, bitwise operators'
- bitwise operators, Visual C
- bitwise operators
- operators [C], bitwise
- ^ operator, bitwise operators
- AND operator
- ampersand operator (&)
- ^ operator
- '& operator, bitwise operators'
ms.assetid: e22127b1-9a2d-4876-b01d-c8f72cec3317
ms.openlocfilehash: 8cbdb5309d5351f77306007e8acd1675be5e2a35
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211578"
---
# <a name="c-bitwise-operators"></a>C 按位运算符

按位运算符执行按位“与”(&  )、按位“异或”(^  ) 和按位“与或”(&#124;  ) 运算。

## <a name="syntax"></a>语法

*AND-expression*: &nbsp;&nbsp;*equality-expression* &nbsp;&nbsp;*AND-expression* **&** *equality-expression*

*exclusive-OR-expression*：&nbsp;&nbsp;*AND-expression* &nbsp;&nbsp;*exclusive-OR-expression* **^** *AND-expression*

*inclusive-OR-expression*: &nbsp;&nbsp;*exclusive-OR-expression* &nbsp;&nbsp;*inclusive-OR-expression* &#124; *exclusive-OR-expression*

按位运算符的操作数必须具有整数类型，但其类型会不同。 这些运算符执行常用算术转换；结果的类型是转换后操作数的类型。

C 按位运算符如下所述：

|运算符|描述|
|--------------|-----------------|
|**&**|按位“与”运算符将其第一操作数的每个位与其第二操作数的相应位进行比较。 如果两个位均为 1，则对应的结果位将设置为 1。 否则，将对应的结果位设置为 0。|
|**^**|按位“异或”运算符将其第一操作数的每个位与其第二操作数的相应位进行比较。 如果一个位是 0，另一个位是 1，则相应的结果位将设置为 1。 否则，将对应的结果位设置为 0。|
|**&#124;**|按位“与或”运算符将其第一操作数的每个位与第二操作数的相应位进行比较。 如果其中一个位是 1，则将对应的结果位设置为 1。 否则，将对应的结果位设置为 0。|

## <a name="examples"></a>示例

这些声明用于以下三个示例：

```C
short i = 0xAB00;
short j = 0xABCD;
short n;

n = i & j;
```

第一个示例中的分配给 `n` 的结果与 `i` 相同（0xAB00 十六进制）。

```C
n = i | j;

n = i ^ j;
```

第二个示例中的按位“与或”生成值 0xABCD（十六进制），而第三个示例中的按位“异或”生成 0xCD（十六进制）。

**Microsoft 专用**

根据 ANSI C 标准，对有符号整数进行的按位运算的结果是实现定义的。 对于 Microsoft C 编译器，对有符号整数进行的按位运算与对无符号整数进行的按位运算的工作原理相同。 例如，`-16 & 99` 可用二进制格式表示

```Expression
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

按位 AND 的结果为 96（十进制）。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[按位 AND 运算符：(&)](../cpp/bitwise-and-operator-amp.md)<br/>
[按位异或运算符：^](../cpp/bitwise-exclusive-or-operator-hat.md)<br/>
[按位“与或”运算符：&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)
