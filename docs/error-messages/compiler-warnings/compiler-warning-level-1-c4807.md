---
description: 了解详细信息：编译器警告 (等级 1) C4807
title: 编译器警告（等级 1）C4807
ms.date: 11/04/2016
f1_keywords:
- C4807
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
ms.openlocfilehash: 4c015d2ee7c566199411374402719c4a8eaee37f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238136"
---
# <a name="compiler-warning-level-1-c4807"></a>编译器警告（等级 1）C4807

“operation”: 类型“type”与类型“type”的有符号位域的混合不安全

将一位有符号位域与变量进行比较时，将生成此警告 **`bool`** 。 因为一位有符号位域只能包含值-1 或0，所以将其与进行比较是危险的 **`bool`** 。 不会生成有关混合 **`bool`** 和一位无符号位域的警告，因为它们与相同， **`bool`** 并且只能包含0或1。

## <a name="example"></a>示例

下面的示例生成 C4807：

```cpp
// C4807.cpp
// compile with: /W1
typedef struct bitfield {
   signed mybit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bool b = true;

   // try..
   // int b = true;

   bf.mybit = -1;
   if (b == bf.mybit) {   // C4807
      b = false;
   }
}
```
