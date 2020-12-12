---
description: 了解详细信息：未处理的 c + + 异常
title: 未处理的 C++ 异常
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], unhandled exceptions
- catch keyword [C++], handler not found
- exceptions [C++], unhandled
- C++ exception handling, unhandled exceptions
- unhandled exceptions [C++]
ms.assetid: 13f09c53-9254-4407-9db9-14e730e047cc
ms.openlocfilehash: 68bd8740d86df3faf4a83b7b2f269def5eeb5eca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145738"
---
# <a name="unhandled-c-exceptions"></a>未处理的 C++ 异常

如果在当前异常中找不到匹配的处理程序 (或省略号 **`catch`** 处理程序) ，则调用预定义的 `terminate` 运行时函数。  (还可以 `terminate` 在任何处理程序中显式调用。 ) 的默认操作 `terminate` 是调用 `abort` 。 如果你希望 `terminate` 在退出应用程序之前调用程序中的某些其他函数，则用被调用函数的名称作为其单个自变量调用 `set_terminate` 函数。 您可以在程序的任何点调用 `set_terminate`。 `terminate`例程始终调用作为的参数提供的最后一个函数 `set_terminate` 。

## <a name="example"></a>示例

以下示例引发 `char *` 异常，但不包含用于捕获类型 `char *` 的异常的指定处理程序。 对 `set_terminate` 的调用指示 `terminate` 调用 `term_func`。

```cpp
// exceptions_Unhandled_Exceptions.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
void term_func() {
   cout << "term_func was called by terminate." << endl;
   exit( -1 );
}
int main() {
   try
   {
      set_terminate( term_func );
      throw "Out of memory!"; // No catch handler for this exception
   }
   catch( int )
   {
      cout << "Integer exception raised." << endl;
   }
   return 0;
}
```

## <a name="output"></a>输出

```Output
term_func was called by terminate.
```

`term_func` 函数最好是通过调用 `exit` 来终止程序或当前线程。 如果它没有这样做，而是返回到其调用方，则调用 `abort`。

## <a name="see-also"></a>请参阅

[异常和错误处理的新式 c + + 最佳做法](../cpp/errors-and-exception-handling-modern-cpp.md)
