---
description: 详细了解：编译器警告 (等级 3) C4290
title: 编译器警告（等级 3）C4290
ms.date: 11/04/2016
f1_keywords:
- C4290
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
ms.openlocfilehash: 771eb01c23778a716aee22ca747ea6473909a8bc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344063"
---
# <a name="compiler-warning-level-3-c4290"></a>编译器警告（等级 3）C4290

已忽略 c + + 异常规范，但指示函数不 __declspec (nothrow) 

函数是使用异常规范声明的，该规范 Visual C++ 接受但不实现。 在编译过程中忽略具有异常规范的代码可能需要重新编译和链接，以便在支持异常规范的未来版本中重复使用。

有关详细信息，请参阅 [异常规范 (throw) ](../../cpp/exception-specifications-throw-cpp.md) 。

可以通过使用 [警告](../../preprocessor/warning.md) 杂注来避免此警告：

```cpp
#pragma warning( disable : 4290 )
```

下面的代码示例生成 C4290：

```cpp
// C4290.cpp
// compile with: /EHs /W3 /c
void f1(void) throw(int) {}   // C4290

// OK
void f2(void) throw() {}
void f3(void) throw(...) {}
```
