---
description: 了解更多：编译器错误 C3536
title: 编译器错误 C3536
ms.date: 11/04/2016
f1_keywords:
- C3536
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
ms.openlocfilehash: 62bd8bb75adfbf0e21f150f4240bb5f4011f6382
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97112500"
---
# <a name="compiler-error-c3536"></a>编译器错误 C3536

"symbol"：初始化之前无法使用

指定的符号在初始化之前不能使用。 在实践中，这意味着无法使用变量来初始化自身。

### <a name="to-correct-this-error"></a>更正此错误

1. 不要使用自身初始化变量。

## <a name="example"></a>示例

下面的示例将生成 C3536，因为每个变量都是自行初始化的。

```cpp
// C3536.cpp
// Compile with /Zc:auto
int main()
{
   auto a = a;     //C3536
   auto b = &b;    //C3536
   auto c = c + 1; //C3536
   auto* d = &d;   //C3536
   auto& e = e;    //C3536
   return 0;
};
```

## <a name="see-also"></a>请参阅

[auto 关键字](../../cpp/auto-cpp.md)
