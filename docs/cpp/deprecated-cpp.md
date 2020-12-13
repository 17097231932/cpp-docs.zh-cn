---
description: '了解更多：弃用的 (c + +) '
title: 已弃用 (C++)
ms.date: 03/28/2017
f1_keywords:
- deprecated_cpp
helpviewer_keywords:
- __declspec keyword [C++], deprecated
- deprecated __declspec keyword
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
ms.openlocfilehash: cd7bc3acbe6a61e87a1766025bcc174268190c48
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339418"
---
# <a name="deprecated-c"></a>已弃用 (C++)

本主题介绍了特定于 Microsoft 的不推荐使用的 declspec 声明。 有关 c + + 14 属性的信息 `[[deprecated]]` ，以及有关何时使用该属性与特定于 Microsoft 的 declspec 或杂注的指导，请参阅 [c + + 标准属性](attributes.md)。

除了下面所述的异常， **`deprecated`** 声明提供了与 [弃用](../preprocessor/deprecated-c-cpp.md) 的杂注相同的功能：

- **`deprecated`** 声明允许您将特定形式的函数重载指定为弃用，而杂注窗体适用于函数名称的所有重载形式。

- **`deprecated`** 声明允许指定在编译时将显示的消息。 该消息的文本可以来自宏。

- 只能使用杂注将宏标记为已弃用 **`deprecated`** 。

如果编译器遇到不推荐使用的标识符或标准 [`[[deprecated]]`](attributes.md) 属性，则会引发 [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) 警告。

## <a name="examples"></a>示例

下面的示例演示在使用已弃用的函数时，如何将函数标记为已弃用以及如何指定在编译时将显示的消息。

```cpp
// deprecated.cpp
// compile with: /W3
#define MY_TEXT "function is deprecated"
void func1(void) {}
__declspec(deprecated) void func1(int) {}
__declspec(deprecated("** this is a deprecated function **")) void func2(int) {}
__declspec(deprecated(MY_TEXT)) void func3(int) {}

int main() {
   func1();
   func1(1);   // C4996
   func2(1);   // C4996
   func3(1);   // C4996
}
```

下面的示例演示在使用已弃用的类时，如何将类标记为已弃用以及如何指定在编译时将显示的消息。

```cpp
// deprecate_class.cpp
// compile with: /W3
struct __declspec(deprecated) X {
   void f(){}
};

struct __declspec(deprecated("** X2 is deprecated **")) X2 {
   void f(){}
};

int main() {
   X x;   // C4996
   X2 x2;   // C4996
}
```

## <a name="see-also"></a>请参阅

[__declspec](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)
