---
description: 了解详细信息： _lock
title: _lock
ms.date: 11/04/2016
api_name:
- _lock
api_location:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lock
- _lock
helpviewer_keywords:
- lock function
- _lock function
ms.assetid: 29f77c37-30de-4b3d-91b6-030216e645a6
ms.openlocfilehash: 9b95c8b7ad0f0ce84348f9581d9acb611373a27b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331041"
---
# <a name="_lock"></a>_lock

获取多线程锁定。

> [!IMPORTANT]
> 此函数已过时。 从 Visual Studio 2015 开始，CRT 中不再提供此函数。

## <a name="syntax"></a>语法

```cpp
void __cdecl _lock
   int locknum
);
```

#### <a name="parameters"></a>parameters

*locknum*<br/>
[in] 要获取的锁定标识符。

## <a name="remarks"></a>备注

如果已获取锁定，则此方法仍获取锁定会导致内部 C 运行时 (CRT) 错误。 如果此方法无法获取锁定，则它将退出并显示错误，同时将错误代码设置为 `_RT_LOCK`。

## <a name="requirements"></a>要求

**源：** mlock.c

## <a name="see-also"></a>请参阅

[字母函数引用](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[_unlock](../c-runtime-library/unlock.md)
