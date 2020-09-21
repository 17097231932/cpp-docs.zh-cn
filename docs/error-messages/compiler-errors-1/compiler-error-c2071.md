---
title: 编译器错误 C2071
ms.date: 11/04/2016
f1_keywords:
- C2071
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
ms.openlocfilehash: 7619d968379bfc35e98bd87071b75296d10c382c
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743277"
---
# <a name="compiler-error-c2071"></a>编译器错误 C2071

"identifier"：非法的存储类

`identifier` 已使用无效的 [存储类](../../c-language/c-storage-classes.md)声明。 为标识符指定多个存储类时或定义与存储类声明不兼容时，会导致此错误。

若要解决此问题，请了解标识符的预期存储类（例如 **`static`** 或）， **`extern`** 并更正要匹配的声明。

## <a name="examples"></a>示例

以下示例生成 C2071。

```cpp
// C2071.cpp
// compile with: /c
struct C {
   extern int i;   // C2071
};
struct D {
   int i;   // OK, no extern on an automatic
};
```

以下示例生成 C2071。

```cpp
// C2071_b.cpp
// compile with: /c
typedef int x(int i) { return i; }   // C2071
typedef int (x)(int);   // OK, no local definition in typedef
```
