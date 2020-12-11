---
description: 详细了解：编译器警告 (等级 3) C4373
title: 编译器警告（等级 3）C4373
ms.date: 11/04/2016
f1_keywords:
- C4373
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
ms.openlocfilehash: a0688f8ed0af1c2854a4449a2fcba31d412a9e4f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160449"
---
# <a name="compiler-warning-level-3-c4373"></a>编译器警告（等级 3）C4373

> "*function*"：虚函数重写 "*base_function*"，当参数只在 const/volatile 限定符上有差异时，早期版本的编译器不会重写

## <a name="remarks"></a>备注

应用程序在派生类中包含一个方法，可重写基类中的虚拟方法，在重写方法中的参数中，只有 [const](../../cpp/const-cpp.md) 或 [volatile](../../cpp/volatile-cpp.md) 限定符与虚拟方法中的参数不同。 这就意味着编译器必须将函数引用绑定到基类或派生类中的方法。

Visual Studio 2008 之前的编译器版本将函数绑定到基类中的方法，然后发出警告消息。 后续版本的编译器忽略 **`const`** 或 **`volatile`** 限定符，将函数绑定到派生类中的方法，然后发出警告 **C4373**。 后一种行为符合 C++ 标准。

## <a name="example"></a>示例

下面的代码示例将生成警告 C4373。 若要解决此问题，你可以使替代使用与基成员函数相同的 CV 限定符，或者，如果你不打算创建替代，则可以为派生类中的函数指定一个不同的名称。

```cpp
// c4373.cpp
// compile with: /c /W3
#include <stdio.h>
struct Base
{
    virtual void f(int i) {
        printf("base\n");
    }
};

struct Derived : Base
{
    void f(const int i) {  // C4373
        printf("derived\n");
    }
};

int main()
{
    Derived d;
    Base* p = &d;
    p->f(1);
}
```

```Output
derived
```
