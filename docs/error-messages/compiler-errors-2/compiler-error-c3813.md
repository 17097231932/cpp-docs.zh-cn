---
description: 了解更多：编译器错误 C3813
title: 编译器错误 C3813
ms.date: 11/04/2016
f1_keywords:
- C3813
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
ms.openlocfilehash: ae7157166083a4a86d9a5b170cbff3e127c87abb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180989"
---
# <a name="compiler-error-c3813"></a>编译器错误 C3813

属性声明只能在托管类型或 WinRT 类型的定义内出现

[属性](../../dotnet/how-to-use-properties-in-cpp-cli.md)只能在托管类型或 Windows 运行时类型内声明。 本机类型不支持 **`property`** 关键字。

## <a name="example"></a>示例

下面的示例生成 C3813，并演示如何修复此错误：

```cpp
// C3813.cpp
// compile by using: cl /c /clr C3813.cpp
class A
{
   property int Int; // C3813
};

ref class B
{
   property int Int; // OK - declared within managed type
};
```
