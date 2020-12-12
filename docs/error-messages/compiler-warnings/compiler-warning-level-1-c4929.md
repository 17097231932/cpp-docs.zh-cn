---
description: 了解详细信息：编译器警告 (等级 1) C4929
title: 编译器警告（等级 1）C4929
ms.date: 11/04/2016
f1_keywords:
- C4929
helpviewer_keywords:
- C4929
ms.assetid: 95f8ab4f-4468-4caa-acd5-8f4592f03b3c
ms.openlocfilehash: 73331759ebdf43694618140985161400ecdafb1e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203544"
---
# <a name="compiler-warning-level-1-c4929"></a>编译器警告（等级 1）C4929

"file"：类型库包含联合;忽略 "embedded_idl" 限定符

[#Import](../../preprocessor/hash-import-directive-cpp.md)的 embedded_idl 属性无法应用于类型库，因为类型库中存在联合。 若要解决此警告，请勿使用 embedded_idl。

## <a name="examples"></a>示例

下面的示例定义了一个组件。

```cpp
// C4929a.cpp
// compile with: /LD /link /TLBOUT:C4929a.tlb
#include <objbase.h>
[module(name="Test")];
[public, switch_type(short)] typedef union _TD_UNION_TYPE   {
   [case(24)]
      float fM;
   [case(25)]
      double dMN;
   [default]
      int x;
} TD_UNION_TYPE;

[export, public] typedef struct _TDW_TYPE {
   [switch_is(sU)] TD_UNION_TYPE w;
      short sU;
} TD_TYPE;

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface I {
   HRESULT f(TD_TYPE*);
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct C : I {
   HRESULT f(TD_TYPE*) { return 0; }
};
```

下面的示例生成 C4929。

```cpp
// C4929b.cpp
// compile with: /c /W1
#import "C4929a.tlb" embedded_idl   // C4929
```
