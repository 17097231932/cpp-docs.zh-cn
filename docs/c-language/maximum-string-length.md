---
description: 详细了解：最大字符串长度
title: 最大字符串长度
ms.date: 11/04/2016
helpviewer_keywords:
- lengths, strings
- string length, maximum
- maximum string length
- strings [C++], length
ms.assetid: 99a80e4a-6212-47b7-a6bd-bdf99bd44928
ms.openlocfilehash: 1da7618a044be2427bd0b0f7f4931287ee4b8014
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243427"
---
# <a name="maximum-string-length"></a>最大字符串长度

**Microsoft 专用**

ANSI 兼容性要求编译器在串联后接受字符串中最多 509 个字符。 Microsoft C 中允许的字符串的最大长度约为 2,048 个字节。 但是，如果字符串由用双引号引起来的多个部分构成，则预处理器会将这些部分串联为一个字符串，对于串联的每个行，它会将一个额外的字节添加到总字节数。

例如，假设字符串包含 40 个行（其中，每行 50 个字符，共 2,000 个字符）和一个包含 7 个字符的行，并且每个行是由双引号引起来的。 所有这些字符共有 2,007 个字节，加上终止 null 字符的 1 个字节，总共为 2,008 个字节。 在串联时，为前 40 个行中的每个行添加一个额外字符。 这样将共有 2,048 个字节。 但请注意，如果使用行继续符 (\\) 代替双引号，则预处理器不会为每个行添加一个额外字符。

单个带引号的字符串的长度不能多于 2048 个字节，可以通过串联多个字符串来构造一个长度约为 65535 个字节的字符串。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[C 字符串文本](../c-language/c-string-literals.md)
