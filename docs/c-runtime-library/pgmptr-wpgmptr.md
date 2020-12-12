---
description: 了解详细信息： _pgmptr、_wpgmptr
title: _pgmptr、_wpgmptr
ms.date: 11/04/2016
f1_keywords:
- pgmptr
- _pgmptr
- wpgmptr
- _wpgmptr
helpviewer_keywords:
- wpgmptr function
- _wpgmptr function
- _pgmptr function
- pgmptr function
ms.assetid: 4d44b515-0eff-4136-8bc4-684195f218f5
ms.openlocfilehash: 70902be4f1c9686839a958439116fc3e28a2a315
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213437"
---
# <a name="_pgmptr-_wpgmptr"></a>_pgmptr、_wpgmptr

可执行文件的路径。 已弃用；使用 [_get_pgmptr](../c-runtime-library/reference/get-pgmptr.md) 和 [_get_wpgmptr](../c-runtime-library/reference/get-wpgmptr.md)。

## <a name="syntax"></a>语法

```
extern char *_pgmptr;
extern wchar_t *_wpgmptr;
```

## <a name="remarks"></a>备注

当程序从命令解释器 (Cmd.exe) 中运行时，`_pgmptr` 将自动初始化为可执行文件的完整路径。 例如，如果 Hello.exe 在 C:\BIN 中，而且 C:\BIN 在路径中，则执行时将 `_pgmptr` 设置为 C:\BIN\Hello.exe。

```
C> hello
```

当程序不是从命令行中运行时，`_pgmptr` 可能将初始化为程序名称（不带文件扩展名的基名称）或文件名称、相对路径或完整路径。

`_wpgmptr` 是 `_pgmptr` 的宽字符版本，可与使用 `wmain` 的程序一起使用。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|

## <a name="requirements"></a>要求

|变量|必需的标头|
|--------------|---------------------|
|`_pgmptr`, `_wpgmptr`|\<stdlib.h>|

## <a name="example"></a>示例

下面的程序说明 `_pgmptr` 的使用。

```c
// crt_pgmptr.c
// compile with: /W3
// The following program demonstrates the use of _pgmptr.
//
#include <stdio.h>
#include <stdlib.h>
int main( void )
{
   printf("The full path of the executing program is : %Fs\n",
     _pgmptr); // C4996
   // Note: _pgmptr is deprecated; use _get_pgmptr instead
}
```

您可通过将 `_wpgmptr` 更改为 `%Fs` 并将 `%S` 更改为 `main`，从而使用 `wmain`。

## <a name="see-also"></a>请参阅

[全局变量](../c-runtime-library/global-variables.md)
