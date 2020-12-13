---
description: 详细了解：编译器警告 (级别 4) C4626
title: 编译器警告（等级 4）C4626
ms.date: 11/04/2016
f1_keywords:
- C4626
helpviewer_keywords:
- C4626
ms.assetid: 7f822ff4-a4a3-4f17-b45b-e8b7b4659a14
ms.openlocfilehash: d528cab5a62abb7e91d4b7bb1487368bd44c6b41
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134207"
---
# <a name="compiler-warning-level-4-c4626"></a>编译器警告（等级 4）C4626

“派生类”：赋值运算符已隐式定义为删除，因为基类赋值运算符不可访问或已被删除

赋值运算符已被删除或在基类中不可访问，因此并未为派生类生成。 分配此类型的对象的任何尝试都将导致编译器错误。

默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。

以下示例生成 C4626，并演示如何对其进行修复：

```
// C4626
// compile with: /W4
#pragma warning(default : 4626)
class B
{
// public:
   B& operator = (const B&)
   {
      return *this;
   }
};

class D : public B
{

}; // C4626 - to fix, make B's copy constructor public

int main()
{
   D m;
   D n;
   // m = n;   // this line will cause an error
}
```
