---
description: 了解详细信息： strict_gs_check 杂注
title: strict_gs_check 杂注
ms.date: 08/29/2019
f1_keywords:
- strict_gs_check
- strict_gs_check_CPP
helpviewer_keywords:
- strict_gs_check pragma
ms.assetid: decfec81-c916-42e0-a07f-8cc26df6a7ce
ms.openlocfilehash: 3fa1600bba59077ff66bfb0184bdd3ca4fe0e326
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197304"
---
# <a name="strict_gs_check-pragma"></a>strict_gs_check 杂注

此杂注提供了增强的安全检查。

## <a name="syntax"></a>语法

> **#pragma strict_gs_check (** [ **push，** ] { **on**  |  **off** } **)**\
> **#pragma strict_gs_check ( pop )**

## <a name="remarks"></a>备注

指示编译器在函数堆栈中插入随机 Cookie 以帮助检测基于堆栈的缓冲区溢出的某些类别。 默认情况下， `/GS` (缓冲区安全检查) 编译器选项不为所有函数插入 cookie。 有关详细信息，请参阅 [/gs (缓冲区安全检查) ](../build/reference/gs-buffer-security-check.md)。

使用进行编译， `/GS` 以启用 **strict_gs_check**。

请在公开给可能有害的数据的代码模块中使用此杂注。 **strict_gs_check** 是一种严格的杂注，适用于可能不需要这种防御的函数，但经过了优化，可以最大程度地降低其对生成的应用程序性能的影响。

即使您使用此杂注，也应尽可能写入安全的代码。 也就是说，请确保代码没有缓冲区溢出。 **strict_gs_check** 可以保护应用程序不受代码中保留的缓冲区溢出的保护。

## <a name="example"></a>示例

在此示例中，当我们将数组复制到本地数组时，会发生缓冲区溢出。 使用编译此代码时 `/GS` ，不会在堆栈中插入 cookie，因为数组数据类型是一个指针。 添加 **strict_gs_check** 杂注会强制堆栈 cookie 进入函数堆栈中。

```cpp
// pragma_strict_gs_check.cpp
// compile with: /c

#pragma strict_gs_check(on)

void ** ReverseArray(void **pData,
                     size_t cData)
{
    // **_ This buffer is subject to being overrun!! _*_
    void _pReversed[20];

    // Reverse the array into a temporary buffer
    for (size_t j = 0, i = cData; i ; --i, ++j)
        // *** Possible buffer overrun!! ***
            pReversed[j] = pData[i];

    // Copy temporary buffer back into input/output buffer
    for (size_t i = 0; i < cData ; ++i)
        pData[i] = pReversed[i];

    return pData;
}
```

## <a name="see-also"></a>请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[/GS（缓冲区安全检查）](../build/reference/gs-buffer-security-check.md)
