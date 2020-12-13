---
description: 了解更多：编译器警告 C4430
title: 编译器警告 C4430
ms.date: 11/04/2016
f1_keywords:
- C4430
helpviewer_keywords:
- C4430
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
ms.openlocfilehash: af214bb0e9d373ee319008f509ba78f5d7ade38b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344297"
---
# <a name="compiler-warning-c4430"></a>编译器警告 C4430

缺少类型说明符 - 假定为 int。 注意： c + + 不支持默认值-int

此错误可能是由于对 Visual Studio 2005 执行的编译器一致性工作引起的：所有声明都必须显式指定类型;不再采用 int。

C4430 始终作为错误发出。  可以通过或/wd 关闭此警告 `#pragma warning` ; 有关详细信息，请参阅[警告](../../preprocessor/warning.md)或[/W、/W0、/W1、/W2、/W3、/W4、/W1、/W2、/W3、/W4、/Wall、/Wd、/WE、/Wo、/Wv、/wx (warning Level) ](../../build/reference/compiler-option-warning-level.md) 。

## <a name="example"></a>示例

下面的示例生成 C4430。

```cpp
// C4430.cpp
// compile with: /c
struct CMyClass {
   CUndeclared m_myClass;  // C4430
   int m_myClass;  // OK
};

typedef struct {
   POINT();   // C4430
   // try the following line instead
   // int POINT();
   unsigned x;
   unsigned y;
} POINT;
```
