---
description: 了解详细信息：编译器警告 (等级 1) C4393
title: 编译器警告（等级 1）C4393
ms.date: 11/04/2016
f1_keywords:
- C4393
helpviewer_keywords:
- C4393
ms.assetid: 353a0539-d1ea-4c1b-8849-c9b321ec9842
ms.openlocfilehash: e68829b7e41cbc1720ceb4dced374a53e97fe8d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212709"
---
# <a name="compiler-warning-level-1-c4393"></a>编译器警告（等级 1）C4393

"var"：常量不会影响 literal 数据成员;掉

[文本](../../extensions/literal-cpp-component-extensions.md)数据成员也被指定为 const。  由于文本数据成员隐含为 const，因此不需要将常量添加到声明。

下面的示例生成 C4393：

```cpp
// C4393.cpp
// compile with: /clr /W1 /c
ref struct Y1 {
   literal const int staticConst = 10;   // C4393
   literal int staticConst2 = 10;   // OK
};
```
