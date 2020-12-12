---
description: 了解更多：编译器错误 C2231
title: 编译器错误 C2231
ms.date: 11/04/2016
f1_keywords:
- C2231
helpviewer_keywords:
- C2231
ms.assetid: 677c5c66-d30f-4c3b-bbb9-760858d56477
ms.openlocfilehash: 159f29529fdcf7253fa1af51951c402df1b21823
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194951"
---
# <a name="compiler-error-c2231"></a>编译器错误 C2231

"."：左操作数指向 "class-key"，使用 "->"

成员选择操作左侧的操作数 (。 ) 是指针，而不是类、结构或联合。

下面的示例生成 C2231:

```c
// C2231.c
struct S {
   int member;
} s, *ps = &s;
int main() {
   ps.member = 0;   // C2231

   // OK
   ps->member = 0;   // crash
   s.member = 0;
}
```
