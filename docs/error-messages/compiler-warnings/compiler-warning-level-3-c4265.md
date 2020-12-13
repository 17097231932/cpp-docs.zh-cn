---
description: 详细了解：编译器警告 (等级 3) C4265
title: 编译器警告（等级 3）C4265
ms.date: 11/04/2016
f1_keywords:
- C4265
helpviewer_keywords:
- C4265
ms.assetid: 20547159-6f30-4cc4-83aa-927884c8bb4c
ms.openlocfilehash: f7ad04d59b9896ce91f4a135f205664885af8f68
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344167"
---
# <a name="compiler-warning-level-3-c4265"></a>编译器警告（等级 3）C4265

"class"：类有虚函数，但析构函数不是虚拟的

如果类具有虚函数，但不包括非虚拟析构函数，则当通过基类指针销毁类时，可能无法正确销毁类型的对象。

默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。

下面的示例生成 C4265：

```cpp
// C4265.cpp
// compile with: /W3 /c
#pragma warning(default : 4265)
class B
{
public:
   virtual void vmf();

   ~B();
   // try the following line instead
   // virtual ~B();
};   // C4265

int main()
{
   B b;
}
```
