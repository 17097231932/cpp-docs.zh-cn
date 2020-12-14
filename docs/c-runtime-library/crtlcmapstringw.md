---
description: 了解详细信息： __crtLCMapStringW
title: __crtLCMapStringW
ms.date: 11/04/2016
api_name:
- __crtLCMapStringW
api_location:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __crtLCMapStringW
helpviewer_keywords:
- __crtLCMapStringW
ms.assetid: 45b4ac0e-438c-4fa3-b4d1-34195f4467d9
ms.openlocfilehash: 57b3f7e961de94d8a3dbd045a1fa1d74681cbfdc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97246740"
---
# <a name="__crtlcmapstringw"></a>__crtLCMapStringW

将一个字符串映射到另一个字符串，以执行指定的与区域设置相关的转换。 此函数还可用于生成输入字符串的排序键。

## <a name="syntax"></a>语法

```cpp
int __crtLCMapStringW(
   LCID    Locale,
   DWORD   dwMapFlags,
   LPCWSTR lpSrcStr,
   int     cchSrc,
   LPWSTR  lpDestStr,
   int     cchDest)
```

#### <a name="parameters"></a>parameters

*区域设置*<br/>
区域设置标识符。 区域设置为字符串映射或排序键生成提供上下文。 应用程序可使用 `MAKELCID` 宏创建区域设置标识符。

*dwMapFlags*<br/>
在字符串或排序键生成期间要使用的转换的类型。

*lpSrcStr*<br/>
指向函数映射或用于排序键生成的源字符串的指针。 假定此参数为 Unicode 字符串。

*cchSrc*<br/>
由 `lpSrcStr` 参数指向的字符串的大小（以字符为单位）。 此计数可包含 null 终止符，也可不包含它。

`cchSrc` 值 -1 指定由 `lpSrcStr` 指向的字符串是以 null 结尾的。 如果是这种情况而且此函数在使用时采用了字符串映射模式，则此函数会自己计算字符串的长度，并以 null 终止存储在 `*lpDestStr`中的映射字符串。

*lpDestStr*<br/>
指向函数将映射字符串或排序键存储到其中的缓冲区的长指针。

*cchDest*<br/>
由 `lpDestStr`指向的缓冲区的大小（以字符为单位）。

## <a name="return-value"></a>返回值

如果 `cchDest` 的值不为零，则写入到缓冲区的字符数（如果指定了 `LCMAP_SORTKEY` ，则为字节数）表示成功。 此计数包括 null 终止符的空间。

如果 `cchDest` 值为零，则接收转换的字符串或排序键所需的缓冲区大小（以字符为单位，如果指定了 `LCMAP_SORTKEY` ，则以字节为单位）表示成功。 此大小包括 null 终止符的空间。

零表示失败。 若要获得扩展的错误信息，请调用 `GetLastError` 函数。

## <a name="remarks"></a>备注

如果 `cchSrc` 大于零且 `lpSrcStr` 是一个以 null 结尾的字符串，则 `__crtLCMapStringW` 将 `cchSrc` 设置为字符串的长度。 然后， `__crtLCMapStringW` 使用指定的参数调用 `LCMapString` 函数的宽字符串 (Unicode) 版本。 有关此函数的参数和返回值的详细信息，请参阅 [LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|__crtLCMapStringW|awint.h|
