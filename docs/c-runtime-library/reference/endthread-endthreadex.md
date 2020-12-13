---
description: 了解详细信息： _endthread、_endthreadex
title: _endthread、_endthreadex
ms.date: 4/2/2020
api_name:
- _endthread
- _endthreadex
- _o__endthread
- _o__endthreadex
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
- _endthread
- endthreadex
- _endthreadex
- endthread
helpviewer_keywords:
- _endthread function
- endthread function
- terminating threads
- endthreadex function
- _endthreadex function
- threading [C++], terminating threads
ms.assetid: 18a91f2f-659e-40b4-b266-ec12dcf2abf5
ms.openlocfilehash: ef74cac4cbe23a021ed8d796f92f2767695eb08e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332833"
---
# <a name="_endthread-_endthreadex"></a>_endthread、_endthreadex

终止线程; **_endthread** 终止由 **_beginthread** 创建的线程，  **_endthreadex** 终止 **_beginthreadex** 创建的线程。

## <a name="syntax"></a>语法

```C
void _endthread( void );
void _endthreadex(
   unsigned retval
);
```

### <a name="parameters"></a>parameters

*retval*<br/>
线程退出代码。

## <a name="remarks"></a>备注

可以显式调用 **_endthread** 或 **_endthreadex** 以终止线程;但是，当线程从作为参数传递给 **_beginthread** 或 **_beginthreadex** 的例程中返回时，将自动调用 **_endthread** 或 **_endthreadex** 。 使用对 **endthread** 或 **_endthreadex** 的调用来终止线程有助于确保正确恢复为线程分配的资源。

> [!NOTE]
> 对于与 Libcmt.lib 链接的可执行文件，请不要调用 Win32 [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) API；这将阻止运行时系统回收已分配的资源。 **_endthread** 和 **_endthreadex** 回收分配的线程资源，然后调用 **ExitThread**。

**_endthread** 会自动关闭线程句柄。  (此行为与 Win32 **ExitThread** api 不同。 ) 因此，当你使用 **_beginthread** 和 **_endthread** 时，请不要通过调用 Win32 [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) api 来显式关闭线程句柄。

与 Win32 **ExitThread** API 一样， **_endthreadex** 不会关闭线程句柄。 因此，当你使用 **_beginthreadex** 和 **_endthreadex** 时，必须通过调用 Win32 **CloseHandle** API 来关闭线程句柄。

> [!NOTE]
> **_endthread** 和 **_endthreadex** 会导致不会调用线程中处于挂起状态的 c + + 析构函数。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_endthread**|\<process.h>|
|**_endthreadex**|\<process.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md) 的多线程版本。

## <a name="example"></a>示例

请参阅 [_beginthread](beginthread-beginthreadex.md) 示例。

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread、_beginthreadex](beginthread-beginthreadex.md)<br/>
