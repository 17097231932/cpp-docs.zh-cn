---
description: 了解更多：编译器错误 C2244
title: 编译器错误 C2244
ms.date: 11/04/2016
f1_keywords:
- C2244
helpviewer_keywords:
- C2244
ms.assetid: d9911c12-ceb5-4f93-ac47-b44a485215c2
ms.openlocfilehash: 9f541eca155b9d728f0bbf7cb1578a6e3424c49c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302231"
---
# <a name="compiler-error-c2244"></a>编译器错误 C2244

"identifier"：无法将函数定义与现有的声明匹配

一元 + 运算符在没有括号的函数调用之前使用过。

此错误仅出现在 c + + 项目中。

下面的示例生成 C2244：

```cpp
// C2244.cpp
int func(char) {
   return 0;
}

int func(int) {
   return 0;
}

int main() {
   +func;   // C2244
}
```

如果对类模板的成员函数使用不正确的函数签名，也会发生 C2244。

```cpp
// C2244b.cpp
// compile with: /c
template<class T>
class XYZ {
   void func(T t);
};

template<class T>
void XYZ<T>::func(int i) {}   // C2244 wrong function signature
// try the following line instead
// void XYZ<T>::func(T t) {}
```

如果将不正确的函数签名用于成员函数模板，也会发生 C2244。

```cpp
// C2244c.cpp
// compile with: /c
class ABC {
   template<class T>
   void func(int i, T t);
};

template<class T>
void ABC::func(int i) {}   // C2244 wrong signature
// try the following line instead
// void ABC::func(int i, T t) {}
```

不能对函数模板进行部分专用化。

```cpp
// C2244d.cpp
template<class T, class U>
class QRS {
   void func(T t, U u);
};

template<class T>
void QRS<T,int>::func(T t, int u) {}   // C2244
```
