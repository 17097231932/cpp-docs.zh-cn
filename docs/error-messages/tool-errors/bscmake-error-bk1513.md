---
description: 了解详细信息： BSCMAKE 错误 BK1513
title: BSCMAKE 错误 BK1513
ms.date: 11/04/2016
f1_keywords:
- BK1513
helpviewer_keywords:
- BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
ms.openlocfilehash: bdf26e3268f98e5ab41ef27bbeaa3734a001671a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238084"
---
# <a name="bscmake-error-bk1513"></a>BSCMAKE 错误 BK1513

非增量更新要求所有的 .SBR 文件

BSCMAKE 无法生成新的浏览信息 (.bsc) 文件，因为一个或多个 .sbr 文件被截断。 若要查找截断的 .sbr 文件的名称，请阅读此错误附带的 [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) 警告。

BSCMAKE 可使用截断的 .sbr 文件更新 .bsc 文件，但不能生成新文件。 BSCMAKE 可能生成新的 .bsc 文件，原因如下：

- 缺少 .bsc 文件。

- 为 .bsc 文件指定的文件名出错。

- .bsc 文件损坏。

若要解决此问题，请删除截断的 .sbr 文件并重新生成，或者清除解决方案并重新生成。  (在 IDE 中，依次选择 " **生成**"、" **清理解决方案**"，然后选择 " **生成**"、" **重新生成解决方案**"。 ) 
