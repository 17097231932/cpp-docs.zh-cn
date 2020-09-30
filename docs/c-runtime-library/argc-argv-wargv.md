---
title: __argc, __argv, __wargv
description: 描述 Microsoft C 运行时库全局常量 __argc 、 __argv 和 __wargv 。
ms.date: 11/04/2016
api_name:
- __wargv
- __argv
- __argc
api_location:
- msvcrt120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __argv
- __argc
- __wargv
helpviewer_keywords:
- __argv
- __wargv
- __argc
ms.assetid: 17001b0a-04ad-4762-b3a6-c54847f02d7c
no-loc:
- __argc
- __argv
- __wargv
- main
- wmain
ms.openlocfilehash: 02c130be0d2dcb8e48d2bb5c75438c94003fc9dd
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507593"
---
# <a name="no-loc__argc-no-loc__argv-no-loc__wargv"></a>__argc, __argv, __wargv

`__argc` 全局变量是传递给程序的命令行参数的数量计数。 `__argv` 是一个指向包含程序参数的单字节字符或多字节字符字符串的数组的指针，`__wargv` 是一个指向包含程序参数的宽字符字符串的数组的指针。 这些全局变量提供了 `main` 或 `wmain` 参数。

## <a name="syntax"></a>语法

```C
extern int __argc;
extern char ** __argv;
extern wchar_t ** __wargv;
```

## <a name="remarks"></a>备注

在使用 `main` 函数的程序中，将在程序启动时通过用于启动该程序的命令行来初始化 `__argc` 和 `__argv`。 会将命令行解析为单个自变量并展开通配符。 会将参数计数分配给 `__argc` 并在堆上分配参数字符串，以及将指向参数数组的指针分配给 `__argv`。 在编译为使用宽字符和 `wmain` 函数的程序中，将解析参数并将通配符展开为宽字符字符串，以及将指向参数字符串的数组的指针分配给 `__wargv`。

对于可移植代码，我们建议你使用传递给 `main` 的参数来获取程序中的命令行参数。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE|已定义 _UNICODE|
|---------------------|---------------------------|-----------------------|
|`__targv`|`__argv`|`__wargv`|

## <a name="requirements"></a>要求

|全局变量|必需的标头|
|---------------------|---------------------|
|`__argc`, `__argv`, `__wargv`|\<stdlib.h>\<cstdlib> (c + +) |

`__argc`、`__argv` 和 `__wargv` 是 Microsoft 扩展。 有关兼容性信息，请参阅[兼容性](../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[全局变量](../c-runtime-library/global-variables.md)\
[main 函数和命令行参数 (c + +) ](../cpp/main-function-command-line-args.md)\
[使用 wmain 而不是 main](../cpp/main-function-command-line-args.md)
