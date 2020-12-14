---
description: 了解更多： c + + 常量表达式
title: C++ 常量表达式
ms.date: 11/04/2016
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
ms.openlocfilehash: 9b7ca098ee5e8c41c2910f41df2031ce7320a514
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253931"
---
# <a name="c-constant-expressions"></a>C++ 常量表达式

*常* 数值是指不会更改的值。 C + + 提供了两个关键字，它们使你能够表达不打算修改对象的意图，还可让你实现该意图。

C++ 需要常量表达式（计算结果为常量的表达式）以便声明：

- 数组边界

- case 语句中的选择器

- 位域长度规范

- 枚举初始值设定项

常量表达式中合法的唯一操作数是：

- 文本

- 枚举常量

- 声明为使用常量表达式初始化的常量的值

- **`sizeof`** 表达

必须将非整型常量（显式或隐式）转换为常量表达式中合法的整型。 因此，以下代码是合法的：

```cpp
const double Size = 11.0;
char chArray[(int)Size];
```

到整型的显式转换在常量表达式中是合法的;所有其他类型和派生类型都是非法的（在用作运算符的操作数时除外） **`sizeof`** 。

逗号运算符和赋值运算符不能用于常量表达式。

## <a name="see-also"></a>请参阅

[表达式的类型](../cpp/types-of-expressions.md)
