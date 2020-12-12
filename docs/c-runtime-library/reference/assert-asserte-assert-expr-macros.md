---
description: 了解详细信息： _ASSERT、_ASSERTE _ASSERT_EXPR 宏
title: _ASSERT、_ASSERTE、_ASSERT_EXPR 宏
ms.date: 11/04/2016
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ASSERTE
- ASSERTE
- _ASSERT_EXPR
helpviewer_keywords:
- debugging [CRT], using macros
- _ASSERTE macro
- macros, debugging with
- debug reporting macros
- _ASSERT macro
- _ASSERT_EXPR macro
ms.assetid: e98fd2a6-7f5e-4aa8-8fe8-e93490deba36
ms.openlocfilehash: 28c90d2c92feb298b2416633e783c5d0a87e4bd8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117570"
---
# <a name="_assert-_asserte-_assert_expr-macros"></a>_ASSERT、_ASSERTE、_ASSERT_EXPR 宏

计算表达式并在结果为 **False** 时生成调试报告 (仅) 调试版本。

## <a name="syntax"></a>语法

```C
// Typical usage:
_ASSERT_EXPR( booleanExpression, message );
_ASSERT( booleanExpression );
_ASSERTE( booleanExpression );
```

### <a name="parameters"></a>parameters

*booleanExpression*<br/>
计算结果不为零 (true) 或为零 (false) 的标量表达式（包括指针表达式）。

*message*<br/>
要显示为报告一部分的宽字符串。

## <a name="remarks"></a>备注

**_ASSERT_EXPR**、 **_ASSERT** 和 **_ASSERTE** 宏为应用程序提供了一个干净且简单的机制，用于在调试过程中检查假设。 它们非常灵活，因为无需包含在 `#ifdef` 语句中，可防止在零售版本的应用程序中调用它们。 这种灵活性使用 [_DEBUG](../../c-runtime-library/debug.md) 宏来实现。 仅当在编译时定义 **_DEBUG** 时， **_ASSERT_EXPR**、 **_ASSERT** 和 **_ASSERTE** 才可用。 未定义 **_DEBUG** 时，将在预处理过程中删除对这些宏的调用。

**_ASSERT_EXPR**、 **_ASSERT** 和 **_ASSERTE** 评估其 *booleanExpression* 参数，并且当结果为 **`false`** (0) 时，它们会打印诊断消息并调用 [_CrtDbgReportW](crtdbgreport-crtdbgreportw.md) 以生成调试报告。 **_ASSERT** 宏打印简单的诊断消息， **_ASSERTE** 在消息中包含失败表达式的字符串表示形式，并且 **_ASSERT_EXPR** 包括诊断消息中的 *消息* 字符串。 如果 *booleanExpression* 的计算结果为非零值，则这些宏不执行任何操作

**_ASSERT_EXPR**、 **_ASSERT** 和 **_ASSERTE** 调用 **_CrtDbgReportW**，这会使所有输出都采用宽字符。 **_ASSERTE** 在 *booleanExpression* 中正确打印 unicode 字符， **_ASSERT_EXPR** 在 *消息* 中打印 unicode 字符。

由于 **_ASSERTE** 宏指定了失败的表达式，而 **_ASSERT_EXPR** 使您能够在生成的报告中指定一条消息，因此，用户可以在不引用应用程序源代码的情况下识别问题。 但存在一个缺点，即每个由 **_ASSERT_EXPR** 打印的 *消息* 和 **_ASSERTE** 计算的每个表达式都以字符串常量的形式包含在应用程序的输出 (调试版本) 文件中。 因此，如果对 **_ASSERT_EXPR** 或 **_ASSERTE** 进行大量调用，则这些表达式可能会大大增加输出文件的大小。

除非使用 [_CrtSetReportMode](crtsetreportmode.md) 和 [_CrtSetReportFile](crtsetreportfile.md) 函数另行指定，否则消息会出现在弹出对话框中，这等于设置以下内容：

```C
_CrtSetReportMode(CRT_ASSERT, _CRTDBG_MODE_WNDW);
````

**_CrtDbgReportW** 基于当前报表模式或为 **_CRT_ASSERT** 报表类型定义的文件，生成调试报告并确定其目标。 默认情况下，断言失败和错误会定向到调试消息窗口。 [_CrtSetReportMode](crtsetreportmode.md) 和 [_CrtSetReportFile](crtsetreportfile.md) 函数用于为每种报告类型定义目标。

当目标是调试消息窗口并且用户单击 " **重试** " 按钮时， **_CrtDbgReportW** 返回1，导致 **_ASSERT_EXPR**、 **_ASSERT** 和 **_ASSERTE** 宏启动调试器（前提是启用了实时 (JIT) 调试。

有关报告过程的详细信息，请参阅 [_CrtDbgReport、_CrtDbgReportW](crtdbgreport-crtdbgreportw.md) 函数。 有关解决断言失败以及将这些宏用作调试错误处理机制的详细信息，请参阅 [使用宏进行验证和报告](/visualstudio/debugger/macros-for-reporting)。

除了 **_ASSERT** 宏以外，还可以使用 [ASSERT](assert-macro-assert-wassert.md) 宏来验证程序逻辑。 此宏可在这些库的调试和发布版本中使用。 [_RPT、_RPTF](rpt-rptf-rptw-rptfw-macros.md) 调试宏还可用于生成调试报告，但它们不计算表达式。 **_RPT** 宏生成一个简单的报表。 **_RPTF** 宏包括在生成的报表中调用报表宏的源文件和行号。 这些宏的宽字符版本可用 (**_RPTW**， **_RPTFW**) 。 宽字符版本与窄字符版本相同，只不过宽字符字符串用于所有字符串参数和输出。

尽管 **_ASSERT_EXPR**、 **_ASSERT** 和 **_ASSERTE** 都是宏并且可通过包含来使用，但是在 \<crtdbg.h> 定义 **_DEBUG** 时，应用程序必须与 C 运行时库的调试版本链接，因为这些宏调用其他运行时函数。

## <a name="requirements"></a>要求

|宏|必需的标头|
|-----------|---------------------|
|**_ASSERT_EXPR**、 **_ASSERT** **_ASSERTE**|\<crtdbg.h>|

## <a name="example"></a>示例

在此程序中，调用 **_ASSERT** 并 **_ASSERTE** 宏来测试该条件 `string1 == string2` 。 如果条件失败，则这些宏会打印诊断消息。 此程序中还会执行 **_RPT** 和 **_RPTF** 宏组，这是 **printf** 函数的替代项。

```C
// crt_ASSERT_macro.c
// compile with: /D_DEBUG /MTd /Od /Zi /link /verbose:lib /debug
//
// This program uses the _ASSERT and _ASSERTE debugging macros.
//

#include <stdio.h>
#include <string.h>
#include <malloc.h>
#include <crtdbg.h>

int main()
{
   char *p1, *p2;

   // The Reporting Mode and File must be specified
   // before generating a debug report via an assert
   // or report macro.
   // This program sends all report types to STDOUT.
   _CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_WARN, _CRTDBG_FILE_STDOUT);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDOUT);
   _CrtSetReportMode(_CRT_ASSERT, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ASSERT, _CRTDBG_FILE_STDOUT);

   // Allocate and assign the pointer variables.
   p1 = (char *)malloc(10);
   strcpy_s(p1, 10, "I am p1");
   p2 = (char *)malloc(10);
   strcpy_s(p2, 10, "I am p2");

   // Use the report macros as a debugging
   // warning mechanism, similar to printf.
   // Use the assert macros to check if the
   // p1 and p2 variables are equivalent.
   // If the expression fails, _ASSERTE will
   // include a string representation of the
   // failed expression in the report.
   // _ASSERT does not include the
   // expression in the generated report.
   _RPT0(_CRT_WARN,
       "Use the assert macros to evaluate the expression p1 == p2.\n");
   _RPTF2(_CRT_WARN, "\n Will _ASSERT find '%s' == '%s' ?\n", p1, p2);
   _ASSERT(p1 == p2);

   _RPTF2(_CRT_WARN, "\n\n Will _ASSERTE find '%s' == '%s' ?\n",
          p1, p2);
   _ASSERTE(p1 == p2);

   _RPT2(_CRT_ERROR, "'%s' != '%s'\n", p1, p2);

   free(p2);
   free(p1);

   return 0;
}
```

```Output
Use the assert macros to evaluate the expression p1 == p2.
crt_ASSERT_macro.c(54) :
Will _ASSERT find 'I am p1' == 'I am p2' ?
crt_ASSERT_macro.c(55) : Assertion failed!
crt_ASSERT_macro.c(58) :

Will _ASSERTE find 'I am p1' == 'I am p2' ?
crt_ASSERT_macro.c(59) : Assertion failed: p1 == p2
'I am p1' != 'I am p2'
```

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[assert 宏、_assert、_wassert](assert-macro-assert-wassert.md)<br/>
[_RPT、_RPTF、_RPTW _RPTFW 宏](rpt-rptf-rptw-rptfw-macros.md)<br/>
