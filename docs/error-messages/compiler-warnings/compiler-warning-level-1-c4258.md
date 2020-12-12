---
description: 了解详细信息：编译器警告 (等级 1) C4258
title: 编译器警告（等级 1）C4258
ms.date: 11/04/2016
f1_keywords:
- C4258
helpviewer_keywords:
- C4258
ms.assetid: bbb75e6d-6693-4e62-8ed3-b006a0ec55e3
ms.openlocfilehash: 1a9bf1fdb6bded2bfad76f25c8bd1bbeadd43bf7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266203"
---
# <a name="compiler-warning-level-1-c4258"></a>编译器警告（等级 1）C4258

"variable"：忽略 for 循环中的定义;使用封闭范围中的定义 "

在 [/ze](../../build/reference/za-ze-disable-language-extensions.md) 和 [/zc： forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)下， [for](../../cpp/for-statement-cpp.md) 循环中定义的变量将在循环结束后超出范围 **`for`** 。 如果在包含循环的作用域中再次使用与 loop 变量同名但在封闭循环中定义的变量，则会出现此警告 **`for`** 。 例如：

```cpp
// C4258.cpp
// compile with: /Zc:forScope /W1
int main()
{
   int i;
   {
      for (int i =0; i < 1; i++)
         ;
      i = 20;   // C4258 i (in for loop) has gone out of scope
   }
}
```
