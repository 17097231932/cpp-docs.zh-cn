---
description: 了解详细信息： BSCMAKE 错误 BK1514
title: BSCMAKE 错误 BK1514
ms.date: 11/04/2016
f1_keywords:
- BK1514
helpviewer_keywords:
- BK1514
ms.assetid: 7c7e2504-a490-44ab-bb1f-47385ee2f4b0
ms.openlocfilehash: c3591187718e6c9e58780edf7affc9e01164f7f7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238032"
---
# <a name="bscmake-error-bk1514"></a>BSCMAKE 错误 BK1514

一切.已截断 .SBR 文件，文件名中未找到任何内容

不是为更新指定的任何 .sbr 文件都是原始浏览信息 ( .bsc) 文件的一部分。 若要查找导致此错误的 .sbr 文件的名称，请阅读其前面的 [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) 警告。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复

1. 为 .sbr 或 .bsc 指定了错误文件名。

1. 受损的 .bsc 文件需要 BSCMAKE 才能重新生成它。
