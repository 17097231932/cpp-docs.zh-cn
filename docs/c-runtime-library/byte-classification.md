---
description: 了解详细信息：字节分类
title: 字节分类
ms.date: 04/04/2018
f1_keywords:
- c.types.bytes
helpviewer_keywords:
- code page 932
- byte classification routines
- bytes, testing
ms.assetid: 1cb52d71-fb0c-46ca-aad7-6472c1103370
ms.openlocfilehash: 00691ca85366c5cbbe28b023f2a269838128fe9e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221691"
---
# <a name="byte-classification"></a>字节分类

其中的每个例程均针对条件满意度测试多字节字符的指定字节。 除非另有指定，否则输出值受区域设置的 LC_CTYPE 类别设置影响；有关详细信息，请参阅 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。 这些不带 **_l** 后缀的函数版本使用此区域设置相关的行为的当前区域设置；带有 **_l** 后缀的版本相同，只不过它们使用传递的区域设置参数。

> [!NOTE]
> 根据定义，0 和 127 之间的 ASCII 字符是所有多字节字符集的子集。 例如，日语的片假名字符集包括 ASCII 以及非 ASCII 字符。

下表中的预定义常量在中定义 \<ctype.h> 。

## <a name="multibyte-character-byte-classification-routines"></a>多字节字符的字节分类例程

|例程所返回的值|字节测试条件|
|-------------|-------------------------|
|[isleadbyte、_isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|前导字节；测试结果取决于当前区域设置的 LC_CTYPE 类别设置|
|[_ismbbalnum、_ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|isalnum &#124;&#124; _ismbbkalnum|
|[_ismbbalpha、_ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|isalpha &#124;&#124; _ismbbkalnum|
|[_ismbbgraph、_ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|与 _ismbbprint 相同，但是 _ismbbgraph 不包含空格字符 (0x20)。|
|[_ismbbkalnum、_ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|标点以外的非 ASCII 文本符号。 例如，仅在代码页 932 中，_ismbbkalnum 测试片假名字母数字。|
|[_ismbbkana、_ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|片假名 (0xA1 - 0xDF)，仅代码页 932|
|[_ismbbkprint、_ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|非 ASCII 文本或非 ASCII 标点符号。 例如，仅在代码页 932 中，_ismbbkprint 测试片假名字母数字或片假名标点（范围：0xA1 - 0xDF）。|
|[_ismbbkpunct、_ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|非 ASCII 标点。 例如，仅在代码页 932 中，_ismbbkpunct 测试片假名标点。|
|[_ismbblead、_ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|多字节字符的第一个字节。 例如，仅在代码页 932 中，有效范围为 0x81 - 0x9F 以及 0xE0 - 0xFC。|
|[_ismbbprint、_ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|isprint &#124; &#124; _ismbbkprint。 ismbbprint 包含空白字符 (0x20)|
|[_ismbbpunct、_ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|ispunct &#124;&#124; _ismbbkpunct|
|[_ismbbtrail、_ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|多字节字符的第二个字节。 例如，仅在代码页 932 中，有效范围为 0x40 - 0x7E 以及 0x80 - 0xEC。|
|[_ismbslead、_ismbslead_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|前导字节（在字符串上下文中）|
|[ismbstrail、_ismbstrail_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|结尾字节（在字符串上下文中）|
|[_mbbtype、_mbbtype_l](../c-runtime-library/reference/mbbtype-mbbtype-l.md)|基于上一个字节返回字节类型|
|[_mbsbtype、_mbsbtype_l](../c-runtime-library/reference/mbsbtype-mbsbtype-l.md)|返回字符串内的字节类型|
|[mbsinit](../c-runtime-library/reference/mbsinit.md)|跟踪多字节字符转换的状态。|

在中定义的 **MB_LEN_MAX** 宏将 \<limits.h> 扩展为任意多字节字符可具有的最大长度（以字节为单位）。 **MB_CUR_MAX**（在中定义 \<stdlib.h> ）将扩展到当前区域设置中任何多字节字符的最大长度（以字节为单位）。

## <a name="see-also"></a>请参阅

[按类别分的通用 C 运行时例程](../c-runtime-library/run-time-routines-by-category.md)
