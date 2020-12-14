---
description: 了解更多： c + + 中的全局常量
title: C++ 中的全局常量
ms.date: 11/04/2016
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
ms.openlocfilehash: 8e960e7e10942fc231fcdeafef6e8d755694c460
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261653"
---
# <a name="global-constants-in-c"></a>C++ 中的全局常量

C + + 全局常量具有静态链接。 这不同于 C。如果尝试在多个文件中使用 c + + 中的全局常量，则会出现未解析的外部错误。 编译器会优化全局常量，而不会为变量保留空间。

解决此错误的一种方法是将 const 初始化包含在头文件中，并在必要时将该标头包括在 CPP 文件中，就像它是函数原型。 另一种可行方法是在对变量进行评估时将其设置为非常量并使用常量引用。

下面的示例生成 C2019：

```cpp
// global_constants.cpp
// LNK2019 expected
void test(void);
const int lnktest1 = 0;

int main() {
   test();
}
```

然后，

```cpp
// global_constants_2.cpp
// compile with: global_constants.cpp
extern int lnktest1;

void test() {
  int i = lnktest1;   // LNK2019
}
```

## <a name="see-also"></a>请参阅

[链接器工具错误 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
