---
title: try-except 语句
description: 对 __try 和 __except 结构化异常处理语句的 Microsoft c + + 引用。
ms.date: 08/25/2020
f1_keywords:
- _abnormal_termination_cpp
- _exception_code_cpp
- _exception_info
- __except
- _except
- _exception_code
- __except_cpp
- _exception_info_cpp
helpviewer_keywords:
- __try keyword [C++]
- EXCEPTION_CONTINUE_EXECUTION macro
- EXCEPTION_CONTINUE_SEARCH macro
- EXCEPTION_EXECUTE_HANDLER macro
- GetExceptionCode function
- try-catch keyword [C++], try-except keyword [C++]
- _exception_code keyword [C++]
- try-except keyword [C++]
- _exception_info keyword [C++]
- _abnormal_termination keyword [C++]
ms.assetid: 30d60071-ea49-4bfb-a8e6-7a420de66381
ms.openlocfilehash: 226c3a3df39f284d9c1267051114fc39db358f55
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898616"
---
# <a name="try-except-statement"></a>`try-except` 语句

`try-except`语句是**Microsoft 特定**的扩展，支持 C 和 c + + 语言中的结构化异常处理。

```cpp
    // . . .
    __try {
        // guarded code
    }
    __except ( /* filter expression */ ) {
        // termination code
    }
    // . . .
```

## <a name="grammar"></a>语法

> *`try-except-statement`*:\
> &emsp;**`__try`** *`compound-statement`* **`__except (`**  *`expression`*  **`)`** *`compound-statement`*

## <a name="remarks"></a>注解

`try-except`语句是 C 和 c + + 语言的 Microsoft 扩展。 它使目标应用程序能够在正常终止程序执行的事件发生时获得控制。 此类事件称为 " *结构化异常*" 或简称为 " *异常* "。 处理这些异常的机制称为 *结构化异常处理* (SEH) 。

有关相关信息，请参阅 [try-finally 语句](../cpp/try-finally-statement.md)。

异常可能基于硬件或基于软件。 即使应用程序无法从硬件或软件异常中完全恢复，结构化异常处理也很有用。 通过 SEH，可以显示错误信息并捕获应用程序的内部状态，从而帮助诊断问题。 它特别适用于无法轻松重现的间歇性问题。

> [!NOTE]
> 结构化异常处理适用于 Win32 中的 C 和 C++ 源文件。 但是，它并不是专门为 c + + 设计的。 您可通过使用 C++ 异常处理来确保提高代码的可移植性。 此外，C++ 异常处理更为灵活，因此它可以处理任何类型的异常。 对于 c + + 程序，我们建议使用本机 c + + 异常处理： [try、catch 和 throw](../cpp/try-throw-and-catch-statements-cpp.md) 语句。

子句后的复合语句 **`__try`** 是 *正文* 或 *受保护* 部分。 **`__except`** 表达式也称为*筛选器*表达式。 其值确定如何处理异常。 `__except` 子句后的复合语句是异常处理程序。 处理程序指定在执行正文部分期间引发异常时要执行的操作。 执行过程如下所示：

1. 执行受保护节。

1. 如果在执行受保护的部分期间没有发生异常，则在 `__except` 子句之后的语句处继续执行。

1. 如果在执行受保护部分或在受保护部分调用的任何例程中发生异常，则 **`__except`** 计算表达式。 有三种可能的值：

   - `EXCEPTION_CONTINUE_EXECUTION` (-1) 异常被消除。 从出现异常的点继续执行。

   - `EXCEPTION_CONTINUE_SEARCH` (0) 异常无法识别。 继续在堆栈中搜索处理程序（首先为包含 `try-except` 语句），然后搜索具有下一个最高优先级的处理程序。

   - `EXCEPTION_EXECUTE_HANDLER` (1) 异常被识别。 通过执行复合语句将控制转移到异常处理程序 **`__except`** ，然后在块后继续执行 **`__except`** 。

**`__except`** 表达式计算为 C 表达式。 它被限制为单个值、条件表达式运算符或逗号运算符。 如果需要更大量的处理，表达式可调用返回上面列出的三个值之一的例程。

每个应用程序都可以有各自的异常处理程序。

跳转到语句中是无效的 **`__try`** ，但跳过一个语句是有效的。 如果进程在执行语句的中间终止，则不会调用异常处理程序 `try-except` 。

为了与早期版本兼容， **_try**、 **_except**和 **_leave** 是、和的同义词， **`__try`** **`__except`** **`__leave`** 除非指定了编译器选项 [/za " \( 禁用语言) 扩展 ](../build/reference/za-ze-disable-language-extensions.md) "。

### <a name="the-__leave-keyword"></a><a name="__leave"></a>`__leave`关键字

**`__leave`** 关键字仅在语句的受保护部分中有效 `try-except` ，其作用是跳转到受保护部分的结尾。 将继续执行异常处理程序后的第一个语句。

**`goto`** 语句还可以跳过受保护的部分，而不会降低性能，因为它在**try finally**语句中。 这是因为不会发生堆栈展开。 但是，我们建议使用 **`__leave`** 关键字而不是 **`goto`** 语句。 原因在于，如果受保护的部分很大或很复杂，则可能导致编程错误。

### <a name="structured-exception-handling-intrinsic-functions"></a>结构化异常处理内部函数

结构化异常处理提供了两个可用于语句的内部函数 `try-except` ： [GetExceptionCode](/windows/win32/Debug/getexceptioncode) 和 [GetExceptionInformation](/windows/win32/Debug/getexceptioninformation)。

`GetExceptionCode` 返回 (一个32位整数) 的代码。

内部函数 `GetExceptionInformation` 返回一个指向 [EXCEPTION_POINTERS](/windows/win32/api/winnt/ns-winnt-exception_pointers) 结构的指针，该结构包含有关异常的其他信息。 通过此指针，您可以访问在出现硬件异常时存在的计算机状态。 结构如下：

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

在 include 文件中定义指针类型和，并 `PEXCEPTION_RECORD` `PCONTEXT` \<winnt.h> `_EXCEPTION_RECORD` `_CONTEXT` 在 include 文件中定义和。 \<excpt.h>

您可以 `GetExceptionCode` 在异常处理程序中使用。 但是，只能 `GetExceptionInformation` 在异常筛选器表达式中使用。 它所指向的信息通常位于堆栈上，并且在控件传输到异常处理程序时不再可用。

内部函数 [AbnormalTermination](/windows/win32/Debug/abnormaltermination) 在终止处理程序中可用。 如果 **try finally** 语句的主体按顺序终止，则返回0。 在所有其他情况下，它将返回 1。

\<excpt.h> 为这些内部函数定义一些替代名称：

`GetExceptionCode` 等效于 `_exception_code`

`GetExceptionInformation` 等效于 `_exception_info`

`AbnormalTermination` 等效于 `_abnormal_termination`

## <a name="example"></a>示例

```cpp
// exceptions_try_except_Statement.cpp
// Example of try-except and try-finally statements
#include <stdio.h>
#include <windows.h> // for EXCEPTION_ACCESS_VIOLATION
#include <excpt.h>

int filter(unsigned int code, struct _EXCEPTION_POINTERS *ep)
{
    puts("in filter.");
    if (code == EXCEPTION_ACCESS_VIOLATION)
    {
        puts("caught AV as expected.");
        return EXCEPTION_EXECUTE_HANDLER;
    }
    else
    {
        puts("didn't catch AV, unexpected.");
        return EXCEPTION_CONTINUE_SEARCH;
    };
}

int main()
{
    int* p = 0x00000000;   // pointer to NULL
    puts("hello");
    __try
    {
        puts("in try");
        __try
        {
            puts("in try");
            *p = 13;    // causes an access violation exception;
        }
        __finally
        {
            puts("in finally. termination: ");
            puts(AbnormalTermination() ? "\tabnormal" : "\tnormal");
        }
    }
    __except(filter(GetExceptionCode(), GetExceptionInformation()))
    {
        puts("in except");
    }
    puts("world");
}
```

### <a name="output"></a>Output

```Output
hello
in try
in try
in filter.
caught AV as expected.
in finally. termination:
        abnormal
in except
world
```

## <a name="see-also"></a>请参阅

[编写异常处理程序](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)
