---
description: 了解更多：编译器错误 C3104
title: 编译器错误 C3104
ms.date: 11/04/2016
f1_keywords:
- C3104
helpviewer_keywords:
- C3104
ms.assetid: b5648d47-e5d3-4b45-a3c0-f46e04eae731
ms.openlocfilehash: b093c5daa96a4c0e9bf789dfcc67ac6b6d3f2561
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116088"
---
# <a name="compiler-error-c3104"></a>编译器错误 C3104

非法的特性参数

你为属性指定了无效的参数。

有关详细信息，请参阅 [Attribute 参数类型](../../extensions/attribute-parameter-types-cpp-component-extensions.md) 。

此错误可能是由于对 Visual Studio 2005 执行的编译器一致性工作所导致的：将托管数组传递到自定义特性时，不再从聚合初始化列表推导数组的类型。 编译器现在要求您指定数组的类型以及初始值设定项列表。

## <a name="examples"></a>示例

下面的示例生成 C3104。

```cpp
// C3104a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::Class)]
public ref struct ABC : public Attribute {
   ABC(array<int>^){}
   array<double> ^ param;
};

[ABC( {1,2,3}, param = {2.71, 3.14})]   // C3104
// try the following line instead
// [ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]
ref struct AStruct{};
```

下面的示例生成 C3104。

```cpp
// C3104b.cpp
// compile with: /clr /c
// C3104 expected
using namespace System;

int func() {
   return 0;
}

[attribute(All)]
ref class A {
public:
   A(int) {}
};

// Delete the following 2 lines to resolve.
[A(func())]
ref class B {};

// OK
[A(0)]
ref class B {};
```
