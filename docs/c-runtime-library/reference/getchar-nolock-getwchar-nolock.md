---
description: 了解详细信息： _getchar_nolock、_getwchar_nolock
title: _getchar_nolock、_getwchar_nolock
ms.date: 11/04/2016
api_name:
- _getchar_nolock
- _getwchar_nolock
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
- getwchar_nolock
- _getwchar_nolock
- _getchar_nolock
- getchar_nolock
helpviewer_keywords:
- _getwchar_nolock function
- getwchar_nolock function
- characters, reading
- _getchar_nolock function
- getchar_nolock function
- standard input, reading from
ms.assetid: dc49ba60-0647-4ae9-aa9a-a0618b1666de
ms.openlocfilehash: 776eb6185cad072e416699e7ec253ab34bd146a2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97256687"
---
# <a name="_getchar_nolock-_getwchar_nolock"></a>_getchar_nolock、_getwchar_nolock

从标准输入读取字符。

## <a name="syntax"></a>语法

```C
int _getchar_nolock( void );
wint_t _getwchar_nolock( void );
```

## <a name="return-value"></a>返回值

请参阅 [getchar、getwchar](getchar-getwchar.md)。

## <a name="remarks"></a>备注

**_getchar_nolock** 和 **_getwchar_nolock** 与 **getchar** 和 **getwchar** 相同，不同之处在于它们不会受到其他线程的干扰。 它们可能更快，因为它们不会产生锁定其他线程的开销。 仅在线程安全的上下文中使用这些函数，如单线程应用程序或调用范围已经处理线程隔离。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_gettchar_nolock**|**_getchar_nolock**|**_getchar_nolock**|**_getwchar_nolock**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_getchar_nolock**|\<stdio.h>|
|**_getwchar_nolock**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 应用中不支持控制台。 与控制台、 **stdin**、 **stdout** 和 **stderr** 关联的标准流句柄必须重定向，然后 C 运行时函数才能在 UWP 应用中使用它们。 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_getchar_nolock.c
// Use _getchar_nolock to read a line from stdin.

#include <stdio.h>

int main()
{
    char buffer[81];
    int i, ch;

    for (i = 0; (i < 80) && ((ch = _getchar_nolock()) != EOF)
                         && (ch != '\n'); i++)
    {
        buffer[i] = (char) ch;
    }

    // Terminate string with a null character

    buffer[i] = '\0';
    printf( "Input was: %s\n", buffer);
}
```

```Output

This textInput was: This text
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[getc、getwc](getc-getwc.md)<br/>
[fgetc、fgetwc](fgetc-fgetwc.md)<br/>
[_getch、_getwch](getch-getwch.md)<br/>
[putc、putwc](putc-putwc.md)<br/>
[ungetc、ungetwc](ungetc-ungetwc.md)<br/>
