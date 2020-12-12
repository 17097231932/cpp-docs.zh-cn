---
description: 了解详细信息： _STATIC_ASSERT 宏
title: _STATIC_ASSERT 宏
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
- _STATIC_ASSERT
helpviewer_keywords:
- _STATIC_ASSERT macro
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
ms.openlocfilehash: bbdb615cccfb245868d4c282acf86c9228ea574b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171194"
---
# <a name="_static_assert-macro"></a>_STATIC_ASSERT 宏

在编译时计算表达式，并在结果为 **FALSE** 时生成错误。

## <a name="syntax"></a>语法

```C
_STATIC_ASSERT(
    booleanExpression
);
```

### <a name="parameters"></a>parameters

*booleanExpression*<br/>
表达式 (包括) 计算结果为非零 (**TRUE**) 或 0 (**FALSE**) 的指针。

## <a name="remarks"></a>备注

此宏类似于 [_ASSERT 和 _ASSERTE 宏](assert-asserte-assert-expr-macros.md)，只是在编译时（而不是在运行时）对 *booleanExpression* 进行计算。 如果 *booleanExpression* 的计算结果为 **FALSE** (0) ，则会生成 [编译器错误 C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) 。

## <a name="example"></a>示例

在此示例中，我们检查 [sizeof](../../c-language/sizeof-operator-c.md) 的是否大于 **`int`** 或等于2字节以及 [sizeof](../../c-language/sizeof-operator-c.md) a 是否 **`long`** 为1字节。 该程序将不会进行编译，并且它将生成 [编译器错误 C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) ，因为大于 **`long`** 1 字节。

```C
// crt__static_assert.c

#include <crtdbg.h>
#include <stdio.h>

_STATIC_ASSERT(sizeof(int) >= 2);
_STATIC_ASSERT(sizeof(long) == 1);  // C2466

int main()
{
    printf("I am sure that sizeof(int) will be >= 2: %d\n",
        sizeof(int));
    printf("I am not so sure that sizeof(long) == 1: %d\n",
        sizeof(long));
}
```

## <a name="requirements"></a>要求

|宏|必需的标头|
|-----------|---------------------|
|**_STATIC_ASSERT**|\<crtdbg.h>|

## <a name="see-also"></a>请参阅

[字母函数引用](crt-alphabetical-function-reference.md)<br/>
[_ASSERT、_ASSERTE _ASSERT_EXPR 宏](assert-asserte-assert-expr-macros.md)<br/>
