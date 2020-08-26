---
title: 调试例程
ms.date: 04/10/2018
f1_keywords:
- c.debug
helpviewer_keywords:
- debugging [CRT], using macros
- macros, debugging with
- debug routines
- debug macros
- debugging [CRT], runtime routines
ms.assetid: cb4d2664-10f3-42f7-a516-595558075471
ms.openlocfilehash: 59e705947856ba9fe9477e88328b1fb2344abb7c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842489"
---
# <a name="debug-routines"></a>调试例程

C 运行时库的调试版本提供了很多诊断服务，便于调试程序并允许开发人员执行以下操作：

- 在调试期间直接执行运行时函数

- 解决断言、错误和异常

- 跟踪堆分配，并防止出现内存泄漏

- 向用户报告调试消息

## <a name="debug-versions-of-the-c-runtime-library-routines"></a>C 运行时库例程的调试版本

若要使用这些例程，必须定义 [_DEBUG](../c-runtime-library/debug.md) 标志。 所有这些例程在零售版本的应用程序中不执行任何操作。 有关如何使用新的调试例程的详细信息，请参阅 [CRT 调试技术](/visualstudio/debugger/crt-debugging-techniques)。

| 例程所返回的值 | 使用 |
|--|--|
| [`_ASSERT`](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) | 计算表达式，并在结果是 FALSE 时生成调试报告 |
| [`_ASSERTE`](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) | 类似于 **`_ASSERT`** ，但在生成的报表中包括失败的表达式 |
| [`_CrtCheckMemory`](../c-runtime-library/reference/crtcheckmemory.md) | 确认在调试堆上分配的内存块的完整性 |
| [`_CrtDbgBreak`](../c-runtime-library/reference/crtdbgbreak.md) | 设置一个断点。 |
| [`_CrtDbgReport`, `_CrtDbgReportW`](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) | 生成具有用户消息的调试报表并将此报表发送到三个可能的目标 |
| [`_CrtDoForAllClientObjects`](../c-runtime-library/reference/crtdoforallclientobjects.md) | 为堆中的所有 `_CLIENT_BLOCK` 类型调用应用程序提供的函数 |
| [`_CrtDumpMemoryLeaks`](../c-runtime-library/reference/crtdumpmemoryleaks.md) | 发生了大量内存泄漏时转储调试堆上的所有内存块 |
| [`_CrtIsMemoryBlock`](../c-runtime-library/reference/crtismemoryblock.md) | 确认指定的内存块位于本地堆，并且具有有效的调试堆块类型标识符 |
| [`_CrtIsValidHeapPointer`](../c-runtime-library/reference/crtisvalidheappointer.md) | 验证指定的指针是否位于本地堆中 |
| [`_CrtIsValidPointer`](../c-runtime-library/reference/crtisvalidpointer.md) | 验证指定的内存范围对于读取和写入是否有效 |
| [`_CrtMemCheckpoint`](../c-runtime-library/reference/crtmemcheckpoint.md) | 获取调试堆的当前状态并将其存储在应用程序提供的 `_CrtMemState` 结构中 |
| [`_CrtMemDifference`](../c-runtime-library/reference/crtmemdifference.md) | 比较两个内存状态的重要差异，并返回结果 |
| [`_CrtMemDumpAllObjectsSince`](../c-runtime-library/reference/crtmemdumpallobjectssince.md) | 在提取指定检查点之后或者在开始执行程序时转储堆上的有关对象的信息 |
| [`_CrtMemDumpStatistics`](../c-runtime-library/reference/crtmemdumpstatistics.md) | 以用户可读的形式转储指定内存状态的调试标头信息 |
| [`_CrtReportBlockType`](../c-runtime-library/reference/crtreportblocktype.md) | 返回与给定调试堆块指针相关联的块类型/子类型。 |
| [`_CrtSetAllocHook`](../c-runtime-library/reference/crtsetallochook.md) | 通过挂钩到 C 运行时调试内存分配过程安装客户端定义的分配函数 |
| [`_CrtSetBreakAlloc`](../c-runtime-library/reference/crtsetbreakalloc.md) | 在指定的对象分配序号上设置断点 |
| [`_CrtSetDbgFlag`](../c-runtime-library/reference/crtsetdbgflag.md) | 检索或修改 `_crtDbgFlag` 标志的状态，以控制调试堆管理器的分配行为 |
| [`_CrtSetDumpClient`](../c-runtime-library/reference/crtsetdumpclient.md) | 安装每次调用调试转储函数来转储 `_CLIENT_BLOCK` 类型内存块时所调用的应用程序定义的函数 |
| [`_CrtSetReportFile`](../c-runtime-library/reference/crtsetreportfile.md) | 标识被 `_CrtDbgReport` 用作特定报表类型的目标的文件或流 |
| [`_CrtSetReportHook`](../c-runtime-library/reference/crtsetreporthook.md) | 通过以下方式安装客户端定义的报告函数：将该函数挂钩到 C 运行时调试报告过程中 |
| [`_CrtSetReportHook2`, `_CrtSetReportHookW2`](../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) | 通过以下方式安装或卸载客户端定义的报告函数：将该函数挂钩到 C 运行时调试报告过程中。 |
| [`_CrtSetReportMode`](../c-runtime-library/reference/crtsetreportmode.md) | 指定由 `_CrtDbgReport` 生成的特定报表类型的一般目标 |
| [_RPT&#91;0,1,2,3,4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) | 通过调用带格式字符串和可变数量参数的 `_CrtDbgReport` 生成调试报表来跟踪应用程序的进度。 提供了无源文件和行号信息。 |
| [_RPTF&#91;0,1,2,3,4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) | 类似于 `_RPTn` 宏，但提供发起报表请求的源文件名和行号 |
| [`_calloc_dbg`](../c-runtime-library/reference/calloc-dbg.md) | 在具有额外空间的堆中为调试标头和覆盖缓冲区分配指定数量的内存块 |
| [`_expand_dbg`](../c-runtime-library/reference/expand-dbg.md) | 通过展开或收缩块调整堆上指定内存块的大小 |
| [`_free_dbg`](../c-runtime-library/reference/free-dbg.md) | 释放堆上的内存块 |
| [`_fullpath_dbg`, `_wfullpath_dbg`](../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md) | 创建指定相对路径名称的绝对或完整路径名称， [`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md) 并使用分配内存。 |
| [`_getcwd_dbg`, `_wgetcwd_dbg`](../c-runtime-library/reference/getcwd-dbg-wgetcwd-dbg.md) | 使用分配内存获取当前工作目录 [`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md) 。 |
| [`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md) | 在具有额外空间的堆中为调试标头和覆盖缓冲区分配内存块 |
| [`_msize_dbg`](../c-runtime-library/reference/msize-dbg.md) | 计算堆上的内存块大小 |
| [`_realloc_dbg`](../c-runtime-library/reference/realloc-dbg.md) | 通过移动和/或调整块的大小重新分配堆上的指定内存块 |
| [`_strdup_dbg`, `_wcsdup_dbg`](../c-runtime-library/reference/strdup-dbg-wcsdup-dbg.md) | 使用分配内存，复制字符串 [`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md) 。 |
| [`_tempnam_dbg`, `_wtempnam_dbg`](../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md) | 生成可用于创建临时文件的名称，可使用 [`_malloc_dbg`](../c-runtime-library/reference/malloc-dbg.md) 来分配内存。 |

## <a name="c-runtime-routines-that-are-not-available-in-source-code-form"></a>无法提供源代码形式的 C 运行时例程

可以使用调试程序逐步完成调试过程中大部分 C 运行时例程的源代码。 但是，Microsoft 认为一些技术是专有的，因此，不会为这些例程的子集提供源代码。 这些例程大多数属于异常处理或浮点处理组，但也包含一些其他例程。 下表列出了这些例程。

:::row:::
   :::column span="":::
      [`acos`](../c-runtime-library/reference/acos-acosf-acosl.md)\
      [`acosh`](../c-runtime-library/reference/acosh-acoshf-acoshl.md)\
      [`asin`](../c-runtime-library/reference/asin-asinf-asinl.md)\
      [`asinh`](../c-runtime-library/reference/asinh-asinhf-asinhl.md)\
      [`atan`, `atan2`](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)\
      [`atanh`](../c-runtime-library/reference/atanh-atanhf-atanhl.md)\
      [`Bessel functions`](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)\
      [`_cabs`](../c-runtime-library/reference/cabs.md)\
      [`ceil`](../c-runtime-library/reference/ceil-ceilf-ceill.md)\
      [`_chgsign`](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)\
      [`_clear87`, `_clearfp`](../c-runtime-library/reference/clear87-clearfp.md)\
      [`_control87`, `_controlfp`](../c-runtime-library/reference/control87-controlfp-control87-2.md)
   :::column-end:::
   :::column span="":::
      [`copysign`](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)\
      [`cos`](../c-runtime-library/reference/cos-cosf-cosl.md)\
      [`cosh`](../c-runtime-library/reference/cosh-coshf-coshl.md)\
      [`Exp`](../c-runtime-library/reference/exp-expf.md)\
      [`fabs`](../c-runtime-library/reference/fabs-fabsf-fabsl.md)\
      [`_finite`](../c-runtime-library/reference/finite-finitef.md)\
      [`floor`](../c-runtime-library/reference/floor-floorf-floorl.md)\
      [`fmod`](../c-runtime-library/reference/fmod-fmodf.md)\
      [`_fpclass`](../c-runtime-library/reference/fpclass-fpclassf.md)\
      [`_fpieee_flt`](../c-runtime-library/reference/fpieee-flt.md)\
      [`_fpreset`](../c-runtime-library/reference/fpreset.md)\
      [`frexp`](../c-runtime-library/reference/frexp.md)
   :::column-end:::
   :::column span="":::
      [`_hypot`](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)\
      [`_isnan`](../c-runtime-library/reference/isnan-isnan-isnanf.md)\
      [`ldexp`](../c-runtime-library/reference/ldexp.md)\
      [`log`](../c-runtime-library/reference/log-logf-log10-log10f.md)\
      [`_logb`](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)\
      [`log10`](../c-runtime-library/reference/log-logf-log10-log10f.md)\
      [`longjmp`](../c-runtime-library/reference/longjmp.md)\
      [`_matherr`](../c-runtime-library/reference/matherr.md)\
      [`modf`](../c-runtime-library/reference/modf-modff-modfl.md)\
      [`_nextafter`](../c-runtime-library/reference/nextafter-functions.md)\
      [`pow`](../c-runtime-library/reference/pow-powf-powl.md)\
      [`printf_s`](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)
   :::column-end:::
   :::column span="":::
      [`printf`](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)\
      [`_scalb`](../c-runtime-library/reference/scalb.md)\
      [`scanf_s`](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)\
      [`scanf`](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)\
      [`setjmp`](../c-runtime-library/reference/setjmp.md)\
      [`sin`](../c-runtime-library/reference/sin-sinf-sinl.md)\
      [`sinh`](../c-runtime-library/reference/sinh-sinhf-sinhl.md)\
      [`sqrt`](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)\
      [`_status87`, `_statusfp`](../c-runtime-library/reference/status87-statusfp-statusfp2.md)\
      [`tan`](../c-runtime-library/reference/tan-tanf-tanl.md)\
      [`tanh`](../c-runtime-library/reference/tanh-tanhf-tanhl.md)
   :::column-end:::
:::row-end:::

尽管为大部分 printf 和 scanf 例程提供源代码，它们仍会对另一个不提供源代码的例程执行内部调用********。

## <a name="routines-that-behave-differently-in-a-debug-build-of-an-application"></a>应用程序调式版本中存在行为差异的例程

从应用程序的调试版本执行调用时，某些 C 运行时函数和 C++ 运算符存在行为差异。  (请注意，可以通过定义 `_DEBUG` 标志或使用 C 运行时库的调试版本链接来完成应用程序的调试版本。 ) 行为差异通常由例程提供的额外功能或信息来支持调试过程。 下表列出了这些例程。

:::row:::
   :::column span="":::
      C [`abort`](../c-runtime-library/reference/abort.md) 例程
   :::column-end:::
   :::column span="":::
      C [`assert`](../c-runtime-library/reference/assert-macro-assert-wassert.md) 例程
   :::column-end:::
   :::column span="":::
      C + + [`delete`](../cpp/delete-operator-cpp.md) 运算符
   :::column-end:::
   :::column span="":::
      C + + [`new`](../cpp/new-operator-cpp.md) 运算符
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>另请参阅

[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)<br/>
[运行时错误检查](../c-runtime-library/run-time-error-checking.md)<br/>
