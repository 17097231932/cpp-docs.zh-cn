---
description: 了解详细信息： _seh_filter_dll、_seh_filter_exe
title: _seh_filter_dll, _seh_filter_exe
ms.date: 4/2/2020
api_name:
- _XcptFilter
- _seh_filter_dll
- _seh_filter_exe
- _o__seh_filter_dll
- _o__seh_filter_exe
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- XcptFilter
- _XcptFilter
- _seh_filter_dll
- _seh_filter_exe
- corecrt_startup/_seh_filter_exe
- corecrt_startup/_seh_filter_dll
helpviewer_keywords:
- XcptFilter function
- _XcptFilter function
- _seh_filter_dll function
- _seh_filter_exe function
ms.assetid: 747e5963-3a12-4bf5-b5c4-d4c1b6068e15
ms.openlocfilehash: f1f297e0ace4a342dcc7370472c1ff1e9f409ce5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288927"
---
# <a name="_seh_filter_dll-_seh_filter_exe"></a>_seh_filter_dll, _seh_filter_exe

标识异常和要采取的相关操作。

## <a name="syntax"></a>语法

```C
int __cdecl _seh_filter_dll(
   unsigned long _ExceptionNum,
   struct _EXCEPTION_POINTERS* _ExceptionPtr
);
int __cdecl _seh_filter_exe(
   unsigned long _ExceptionNum,
   struct _EXCEPTION_POINTERS* _ExceptionPtr
);
```

### <a name="parameters"></a>parameters

*_ExceptionNum*<br/>
异常的标识符。

*_ExceptionPtr*<br/>
指向异常信息的指针。

## <a name="return-value"></a>返回值

用于依据异常处理的结果指示要采取的操作的整数。

## <a name="remarks"></a>备注

这些方法由 [try-except Statement](../../cpp/try-except-statement.md)的异常筛选器表达式调用。 该方法查询固定的内部表来标识异常并确定适当的操作，如下所示。 异常编号在 winnt.h 中定义，信号编号在 signal.h 中定义。

|异常编号 (unsigned long)|信号编号|
|----------------------------------------|-------------------|
|STATUS_ACCESS_VIOLATION|SIGSEGV|
|STATUS_ILLEGAL_INSTRUCTION|SIGILL|
|STATUS_PRIVILEGED_INSTRUCTION|SIGILL|
|STATUS_FLOAT_DENORMAL_OPERAND|SIGFPE|
|STATUS_FLOAT_DIVIDE_BY_ZERO|SIGFPE|
|STATUS_FLOAT_INEXACT_RESULT|SIGFPE|
|STATUS_FLOAT_INVALID_OPERATION|SIGFPE|
|STATUS_FLOAT_OVERFLOW|SIGFPE|
|STATUS_FLOAT_STACK_CHECK|SIGFPE|
|STATUS_FLOAT_UNDERFLOW|SIGFPE|

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

**标头：** corecrt_startup.h

## <a name="see-also"></a>请参阅

[字母函数引用](crt-alphabetical-function-reference.md)<br/>
