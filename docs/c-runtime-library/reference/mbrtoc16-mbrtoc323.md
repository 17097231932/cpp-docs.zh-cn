---
description: 了解详细信息： mbrtoc16、mbrtoc32
title: mbrtoc16、mbrtoc323
ms.date: 4/2/2020
api_name:
- mbrtoc16
- mbrtoc32
- _o_mbrtoc16
- _o_mbrtoc32
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
ms.openlocfilehash: 4132be867186567b31c9e297e6acb4ada68a66ca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178610"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

将字符串中的第一个 UTF-8 多字节字符转换为等效的 UTF-16 或 UTF-32 字符。

## <a name="syntax"></a>语法

```C
size_t mbrtoc16(
   char16_t* destination,
   const char* source,
   size_t max_bytes,
   mbstate_t* state
);

size_t mbrtoc32(
   char32_t* destination,
   const char* source,
   size_t max_bytes,
   mbstate_t* state
);
```

### <a name="parameters"></a>parameters

*位置*\
一个指针，指向要 **`char16_t`** **`char32_t`** 转换的 utf-8 多字节字符的或等效项。 如果为 null，则该函数不存储值。

*源程序*\
指向要转换的 UTF-8 多字节字符字符串的指针。

*max_bytes*\
用于检查要转换的字符的 *源* 中的最大字节数。 此参数的值应为1到1之间的值（包括任何 null 终止符）（ *源* 中剩余）。

*状态*\
指向用于将 UTF-8 多字节字符串解释为一个或多个输出字符的 **mbstate_t** 转换状态对象的指针。

## <a name="return-value"></a>返回值

如果成功，则返回在给定当前 *状态* 值的情况下应用的第一个条件的值：

|值|条件|
|-----------|---------------|
|0|*从源* 转换的下一个 *max_bytes* 或更少字符对应于空宽字符，这是在 *目标* 不为 null 时存储的值。<br /><br /> *状态* 包含初始移位状态。|
|介于1和 *max_bytes* 之间（含）|返回的值是完成有效多字节字符的 *源* 字节数。 如果 *destination* 不为 null，则存储转换后的宽字符。|
|-3|如果 *目标* 不为 null，则以前对函数的调用生成的下一个宽字符存储在 *目标* 中。 此调用不会将 *源* 中的任何字节用于该函数。<br /><br /> 当  *源* 指向需要多个宽字符表示 (例如，代理项对) 的 utf-8 多字节字符时，会更新 *状态* 值，以便下一个函数调用写出其他字符。|
|-2|接下来的 *max_bytes* 字节表示不完整但可能有效的 utf-8 多字节字符。 *目标* 中没有存储任何值。 如果 *max_bytes* 为零，则会出现此结果。|
|-1|发生编码错误。 下一个 *max_bytes* 或更少的字节不涉及完整且有效的 utf-8 多字节字符。 *目标* 中没有存储任何值。<br /><br /> **Eilseq 且** 存储在 **errno** 中，并且未指定转换状态值 *状态* 。|

## <a name="remarks"></a>备注

**Mbrtoc16** 函数 *从源* 中读取最多 *max_bytes* 个字节，以查找第一个完整的、有效的 utf-8 多字节字符，然后将等效的 utf-16 字符存储在 *目标* 中。 如果字符需要多个 UTF-16 输出字符，如代理项对，则将 *状态* 值设置为在下一次调用 **mbrtoc16** 时将下一个 utf-16 字符存储在 *目标* 中。 **Mbrtoc32** 函数相同，但输出存储为32字符。

如果 *source* 为 null，则这些函数将返回对 *目标* 使用 **null** 参数进行调用的等效项， `""` (*源* 的空的 null 终止字符串) ，并为 *max_bytes* 提供1。 将忽略 *目标* 和 *max_bytes* 的传递值。

如果 *源* 不为 null，则函数将从字符串的开头开始，并检查最多 *max_bytes* 个字节，以确定完成下一个 utf-8 多字节字符（包括任何移位序列）所需的字节数。 如果检查的字节包含有效且完整的 UTF-8 多字节字符，则该函数将字符转换为等效的16位或32位宽字符。 如果 *destination* 不为 null，则该函数将存储第一个 (，可能只存储目标中) 的结果字符。 如果需要其他输出字符，则将值设置为 " *状态*"，以便对函数的后续调用输出其他字符并返回值-3。 如果不需要其他输出字符，则 *状态* 设置为初始移位状态。

若要将非 UTF-8 多字节字符转换为 UTF-16 LE 字符，请使用 [mbrtowc](mbrtowc.md)、 [mbtowc 或 _mbtowc_l](mbtowc-mbtowc-l.md) 函数。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|C 标头|C++ 标头|
|--------------|--------------|------------------|
|**mbrtoc16**、 **mbrtoc32**|\<uchar.h>|\<cuchar>|

有关其他兼容性信息，请参阅[兼容性](../compatibility.md)。

## <a name="see-also"></a>请参阅

[数据转换](../data-conversion.md)\
[本地](../locale.md)\
[多字节字符序列的解释](../interpretation-of-multibyte-character-sequences.md)\
[c16rtomb、c32rtomb](c16rtomb-c32rtomb1.md)\
[mbrtowc](mbrtowc.md)\
[mbsrtowcs](mbsrtowcs.md)\
[mbsrtowcs_s](mbsrtowcs-s.md)
