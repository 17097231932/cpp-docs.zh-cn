---
description: '了解详细信息：抽象类 (c + +) '
title: 抽象类 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- classes [C++], abstract
- base classes [C++], abstract classes [C++]
- abstract classes [C++]
- derived classes [C++], abstract classes [C++]
ms.assetid: f0c5975b-39de-4d68-9640-6ce57f4632e6
ms.openlocfilehash: bb1c42ce7930128e72c88afaca90da7aaac0bde5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288407"
---
# <a name="abstract-classes-c"></a>抽象类 (C++)

抽象类作为可从中派生更具体的类的一般概念的表达。 您不能创建抽象类类型的对象；但可以使用指向抽象类类型的指针和对它们的引用。

包含至少一个纯虚函数的类被视为抽象类。 派生自抽象类的类必须实现纯虚函数或者它们必须也是抽象类。

请考虑 [虚拟函数](../cpp/virtual-functions.md)中显示的示例。 类 `Account` 的用途是提供通用功能，但 `Account` 类型的对象太通用，因此没什么用。 因此，`Account` 是抽象类的很合适的候选项：

```cpp
// deriv_AbstractClasses.cpp
// compile with: /LD
class Account {
public:
   Account( double d );   // Constructor.
   virtual double GetBalance();   // Obtain balance.
   virtual void PrintBalance() = 0;   // Pure virtual function.
private:
    double _balance;
};
```

此声明与上一个声明的唯一区别是，`PrintBalance` 是用 pure 说明符 (`= 0`) 声明的。

## <a name="restrictions-on-abstract-classes"></a>抽象类限制

抽象类不能用于：

- 变量或成员数据

- 自变量类型

- 函数返回类型

- 显式转换的类型

另一个限制是，如果抽象类的构造函数调用一个纯虚函数，无论是直接还是间接方式，则结果都是不确定的。 但是，抽象类的构造函数和析构函数都可以调用其他成员函数。

可以为抽象类定义纯虚函数，但是只能通过使用以下语法直接调用：

*抽象类名*：：*函数名* ( # A1

这有助于设计基类包括纯虚析构函数的类层次结构，因为在销毁对象的过程中始终会调用基类析构函数。 请看下面的示例：

```cpp
// Declare an abstract base class with a pure virtual destructor.
// deriv_RestrictionsonUsingAbstractClasses.cpp
class base {
public:
    base() {}
    virtual ~base()=0;
};

// Provide a definition for destructor.
base::~base() {}

class derived:public base {
public:
    derived() {}
    ~derived(){}
};

int main() {
    derived *pDerived = new derived;
    delete pDerived;
}
```

删除 `pDerived` 指向的对象时，将调用类 `derived` 的析构函数，然后调用类 `base` 的析构函数。 纯虚函数的空实现确保至少函数的某个实现存在。

> [!NOTE]
> 在前面的示例中，纯虚函数 `base::~base` 是从 `derived::~derived` 隐式调用的。 还可使用完全限定的成员函数名称显式调用纯虚函数。

## <a name="see-also"></a>另请参阅

[继承](../cpp/inheritance-cpp.md)
