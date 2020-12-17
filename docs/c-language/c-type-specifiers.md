---
description: 详细了解：C 类型说明符
title: C 类型说明符
ms.date: 01/29/2018
helpviewer_keywords:
- type specifiers, C
- specifiers, type
ms.assetid: fbe13441-04c3-4829-b047-06d374adc2b6
ms.openlocfilehash: afff33e385564f5ef8d04988255a239135be13b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214199"
---
# <a name="c-type-specifiers"></a>C 类型说明符

声明中的类型说明符定义变量或函数声明的类型。

## <a name="syntax"></a>语法

type-specifier: &nbsp;&nbsp;&nbsp;&nbsp;`void` &nbsp;&nbsp;&nbsp;&nbsp;`char` &nbsp;&nbsp;&nbsp;&nbsp;`short` &nbsp;&nbsp;&nbsp;&nbsp;`int` &nbsp;&nbsp;&nbsp;&nbsp;`long` &nbsp;&nbsp;&nbsp;&nbsp;`float` &nbsp;&nbsp;&nbsp;&nbsp;`double` &nbsp;&nbsp;&nbsp;&nbsp;`signed` &nbsp;&nbsp;&nbsp;&nbsp;`unsigned` &nbsp;&nbsp;&nbsp;&nbsp;struct-or-union-specifier &nbsp;&nbsp;&nbsp;&nbsp;enum-specifier &nbsp;&nbsp;&nbsp;&nbsp;typedef-name

`signed char`、`signed int`、`signed short int` 和 signed long int 类型以及它们对应的 `unsigned` 和 `enum` 一起称为“整型类型”。 `float`、`double` 和 `long double` 类型说明符称为“浮点”或“浮点类型”。 可在变量或函数声明中使用任何整型或浮点型说明符。 如果在声明中没有提供 type-specifier，则将其视为 `int`。

可选关键字 `signed` 和 `unsigned` 可位于任何整型类型的前面或后面（`enum` 除外），还可以单独用作类型说明符（在这种情况下，它们分别被理解为 `signed int` 和 `unsigned int`）。 单独使用时，关键字 `int` 被假定为 `signed`。 单独使用时，关键字 `long` 和 `short` 被理解为 long int 和 `short int`。

枚举类型被视为基本类型。 [枚举声明](../c-language/c-enumeration-declarations.md)中讨论了枚举类型的类型说明符。

关键字 `void` 有三种用途：一是指定函数返回类型，二是为不接受参数的函数指定参数类型列表，三是指定一个指向未指定的类型的指针。 可以使用 `void` 类型来声明不返回值的函数，或声明指向未指定的类型的指针。 若要了解单独出现在函数名称后面的括号中的 `void`，请参阅[参数](../c-language/arguments.md)。

**Microsoft 专用**

类型检查现在符合 ANSI；也就是说，`short` 类型和 `int` 类型是不同的类型。 例如，下面是编译器的早期版本接受的 Microsoft C 编译器中的一个重新定义。

```C
int   myfunc();
short myfunc();
```

下一个示例还会生成有关到不同类型的间接寻址的警告：

```C
int *pi;
short *ps;

ps = pi;  /* Now generates warning */
```

Microsoft C 编译器还生成保留符号的差异警告。 例如：

```C
signed int *pi;
unsigned int *pu

pi = pu;  /* Now generates warning */
```

对类型 `void` 表达式计算副作用。 不能以任何方式使用类型为 `void` 的表达式的（不存在的）值，也不能将 `void` 表达式转换为除 `void` 以外的任何类型（通过隐式或显式转换）。 如果你确实在需要 `void` 表达式的上下文中使用了其他任何类型的表达式，则其值将被放弃。

为了符合 ANSI 规范，void\*\* 不能用作 int\*\*。 只有 `void`\* 才能用作指向未指定的类型的指针。

**结束 Microsoft 专用**

可以使用 `typedef` 声明创建额外的类型说明符，如 [Typedef 声明](../c-language/typedef-declarations.md)中所述。 有关每个类型的大小的信息，请参阅[基本类型的存储](../c-language/storage-of-basic-types.md)。

## <a name="see-also"></a>请参阅

[声明和类型](../c-language/declarations-and-types.md)
