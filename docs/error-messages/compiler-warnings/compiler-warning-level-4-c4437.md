---
description: 详细了解：编译器警告 (级别 4) C4437
title: 编译器警告（等级 4）C4437
ms.date: 11/04/2016
f1_keywords:
- C4437
helpviewer_keywords:
- C4437
ms.assetid: dc07e350-20eb-474c-a7ad-f841ae7ec339
ms.openlocfilehash: 6ea94a972c08dfa6752c5c165a9c547419b03334
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251422"
---
# <a name="compiler-warning-level-4-c4437"></a>编译器警告（等级 4）C4437

从虚拟基 "class1" 到 "class2" 的 dynamic_cast 可能在某些上下文中通过/vd2 编译失败，或定义 "class2"，#pragma vtordisp (2) 生效

默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。

编译器遇到 **`dynamic_cast`** 具有以下特征的操作。

- 转换是从基类指针到派生类的指针。

- 派生类虚拟继承基类。

- 派生类没有虚拟基的 `vtordisp` 字段。

- 在派生类的构造函数或析构函数中找不到该强制转换，或者某个类进一步继承自派生类 (否则，将) 发出编译器警告 C4436。

警告表明，如果在 **`dynamic_cast`** 部分构造的对象上操作，则可能无法正常执行。  当通过继承在警告中命名的派生类的类的构造函数或析构函数调用封闭函数时，会发生这种情况。  如果在警告中命名的派生类绝不会进一步派生，或在对象构造或析构期间不调用封闭函数，则可以忽略此警告。

## <a name="example"></a>示例

下面的示例生成 C4437，并演示从缺少的字段中生成的代码生成问题 `vtordisp` 。

```cpp
// C4437.cpp
// To see the warning and runtime assert, compile with: /W4
// To eliminate the warning and assert, compile with: /W4 /vd2
//       or compile with: /W4 /DFIX
#pragma warning(default : 4437)
#include <cassert>

struct A
{
public:
    virtual ~A() {}
};

#if defined(FIX)
#pragma vtordisp(push, 2)
#endif
struct B : virtual A
{
    B()
    {
        func();
    }

    void func()
    {
        A* a = static_cast<A*>(this);
        B* b = dynamic_cast<B*>(a);     // C4437
        assert(this == b);              // assert unless compiled with /vd2
    }
};
#if defined(FIX)
#pragma vtordisp(pop)
#endif

struct C : B
{
    int i;
};

int main()
{
    C c;
}
```

## <a name="see-also"></a>请参阅

[dynamic_cast 运算符](../../cpp/dynamic-cast-operator.md)<br/>
[vtordisp](../../preprocessor/vtordisp.md)<br/>
[编译器警告 (等级 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)
