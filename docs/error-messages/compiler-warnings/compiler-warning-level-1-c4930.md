---
description: 了解详细信息：编译器警告 (等级 1) C4930
title: 编译器警告（等级 1）C4930
ms.date: 11/04/2016
f1_keywords:
- C4930
helpviewer_keywords:
- C4930
ms.assetid: 89a206c9-c536-4186-8e81-1cde3e7f4f5b
ms.openlocfilehash: 9111b87ee2b281c7781e7115330634daefb14cc4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328071"
---
# <a name="compiler-warning-level-1-c4930"></a>编译器警告（等级 1）C4930

"原型"：未调用原型函数 (是否打算使用变量定义？ ) 

编译器检测到未使用的函数原型。 如果原型旨在用作变量声明，请删除左/右括号。

下面的示例生成 C4930：

```cpp
// C4930.cpp
// compile with: /W1
class Lock {
public:
   int i;
};

void f() {
   Lock theLock();   // C4930
   // try the following line instead
   // Lock theLock;
}

int main() {
}
```

当编译器无法区分函数原型声明和函数调用时，也会发生 C4930。

下面的示例生成 C4930：

```cpp
// C4930b.cpp
// compile with: /EHsc /W1

class BooleanException
{
   bool _result;

public:
   BooleanException(bool result)
      : _result(result)
   {
   }

   bool GetResult() const
   {
      return _result;
   }
};

template<class T = BooleanException>
class IfFailedThrow
{
public:
   IfFailedThrow(bool result)
   {
      if (!result)
      {
         throw T(result);
      }
   }
};

class MyClass
{
public:
   bool MyFunc()
   {
      try
      {
         IfFailedThrow<>(MyMethod()); // C4930

         // try one of the following lines instead
         // IfFailedThrow<> ift(MyMethod());
         // IfFailedThrow<>(this->MyMethod());
         // IfFailedThrow<>((*this).MyMethod());

         return true;
      }
      catch (BooleanException e)
      {
         return e.GetResult();
      }
   }

private:
   bool MyMethod()
   {
      return true;
   }
};

int main()
{
   MyClass myClass;
   myClass.MyFunc();
}
```

在上面的示例中，采用零个参数的方法的结果将作为参数传递到未命名的局部类变量的构造函数。 通过命名局部变量或使用对象实例作为方法调用的前缀以及适当的指针到成员运算符，可以消除调用的歧义。
