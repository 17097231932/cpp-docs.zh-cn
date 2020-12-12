---
description: '了解有关详细信息，请参阅如何：在 c + +/CLI (用 interior_ptr 关键字声明值类型) '
title: 如何：用 interior_ptr 关键字声明值类型 (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- _ptr keyword
- value types, declaring
ms.assetid: 49eea66e-eeba-49bd-95b0-ba297be436e3
ms.openlocfilehash: b8d5c554f212a9536b0ad063d67e044c08194015
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119169"
---
# <a name="how-to-declare-value-types-with-the-interior_ptr-keyword-ccli"></a>如何：用 interior_ptr 关键字声明值类型 (C++/CLI)

interior_ptr 可以用于值类型。

> [!IMPORTANT]
> `/clr` 编译器选项支持此语言功能，但是 `/ZW` 编译器选项不支持此语言功能。

## <a name="example-interior_ptr-with-value-type"></a>示例：值类型 interior_ptr

### <a name="description"></a>描述

下面的 C++/CLI 示例展示了如何将 interior_ptr 用于值类型。

### <a name="code"></a>代码

```cpp
// interior_ptr_value_types.cpp
// compile with: /clr
value struct V {
   V(int i) : data(i){}
   int data;
};

int main() {
   V v(1);
   System::Console::WriteLine(v.data);

   // pointing to a value type
   interior_ptr<V> pv = &v;
   pv->data = 2;

   System::Console::WriteLine(v.data);
   System::Console::WriteLine(pv->data);

   // pointing into a value type
   interior_ptr<int> pi = &v.data;
   *pi = 3;
   System::Console::WriteLine(*pi);
   System::Console::WriteLine(v.data);
   System::Console::WriteLine(pv->data);
}
```

```Output
1
2
2
3
3
3
```

## <a name="example-this-pointer"></a>示例： this 指针

### <a name="description"></a>描述

在值类型中， **`this`** 指针的计算结果为 interior_ptr。

在值类型的非静态成员函数体中 `V` ， **`this`** 是类型的表达式， `interior_ptr<V>` 其值是要为其调用函数的对象的地址。

### <a name="code"></a>代码

```cpp
// interior_ptr_value_types_this.cpp
// compile with: /clr /LD
value struct V {
   int data;
   void f() {
      interior_ptr<V> pv1 = this;
      // V* pv2 = this;   error
   }
};
```

## <a name="example-address-of-operator"></a>示例： address 运算符

### <a name="description"></a>描述

下面的示例演示了如何将 address-of 运算符与静态成员一起使用。

静态 Visual C++ 类型成员的地址产生本机指针。  静态值类型成员的地址是托管指针，因为值类型成员在运行时堆上分配，并且可由垃圾回收器移动。

### <a name="code"></a>代码

```cpp
// interior_ptr_value_static.cpp
// compile with: /clr
using namespace System;
value struct V { int i; };

ref struct G {
   static V v = {22};
   static int i = 23;
   static String^ pS = "hello";
};

int main() {
   interior_ptr<int> p1 = &G::v.i;
   Console::WriteLine(*p1);

   interior_ptr<int> p2 = &G::i;
   Console::WriteLine(*p2);

   interior_ptr<String^> p3 = &G::pS;
   Console::WriteLine(*p3);
}
```

```Output
22
23
hello
```

## <a name="see-also"></a>请参阅

[interior_ptr (c + +/CLI) ](interior-ptr-cpp-cli.md)
