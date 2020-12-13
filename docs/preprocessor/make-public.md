---
description: 了解详细信息： make_public 杂注
title: make_public 杂注
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.make_public
- make_public_CPP
helpviewer_keywords:
- pragmas, make_public
- make_public pragma
ms.assetid: c3665f4d-268a-4932-9661-c37c8ae6a341
ms.openlocfilehash: 327a9882e13f9c51182e0673443566b56177d320
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333407"
---
# <a name="make_public-pragma"></a>make_public 杂注

指示本机类型应具有公共程序集可访问性。

## <a name="syntax"></a>语法

> **(类型 make_public #pragma**  **)**

### <a name="parameters"></a>parameters

*type*\
要具有公共程序集可访问性的类型的名称。

## <a name="remarks"></a>备注

当要引用的本机类型来自无法更改的标头文件时， **make_public** 非常有用。 如果要在具有公共程序集可见性的类型中的公共函数签名中使用本机类型，则本机类型还必须具有公共程序集可访问性，否则编译器将发出警告。

必须在全局范围内指定 **make_public** 。 它仅从其声明到源代码文件末尾的点起生效。

本机类型可以隐式或显式私有。 有关详细信息，请参阅 [类型可见性](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)。

## <a name="examples"></a>示例

下面的示例是包含两个本机结构的定义的头文件的内容。

```cpp
// make_public_pragma.h
struct Native_Struct_1 { int i; };
struct Native_Struct_2 { int i; };
```

下面的代码示例使用头文件。 其中显示，除非你使用 **make_public** 将本机结构显式标记为公共，否则当你尝试在公共托管类型中的公共函数签名中使用本机结构时，编译器将生成警告。

```cpp
// make_public_pragma.cpp
// compile with: /c /clr /W1
#pragma warning (default : 4692)
#include "make_public_pragma.h"
#pragma make_public(Native_Struct_1)

public ref struct A {
   void Test(Native_Struct_1 u) {u.i = 0;}   // OK
   void Test(Native_Struct_2 u) {u.i = 0;}   // C4692
};
```

## <a name="see-also"></a>请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
