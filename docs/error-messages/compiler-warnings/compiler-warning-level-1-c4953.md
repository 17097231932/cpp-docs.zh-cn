---
description: 了解详细信息：编译器警告 (等级 1) C4953
title: 编译器警告（等级 1）C4953
ms.date: 08/27/2018
f1_keywords:
- C4953
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
ms.openlocfilehash: 1f10f757297bd4b0e71ec5246024a3ce7a313689
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327936"
---
# <a name="compiler-warning-level-1-c4953"></a>编译器警告（等级 1）C4953

> 自收集配置文件数据后已编辑被内联方 "*function*"，未使用配置文件数据

当使用 [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)时，编译器检测到在 `/LTCG:PGINSTRUMENT` 之后重新编译的一个输入模块，该模块具有编辑过的函数 (*function*)，在该模块内，现有测试运行将该函数标识为内联的候选项。 但是，重新编译该模块后，此函数不再是内联的候选项。

此警告为信息性。 若要解决此警告，请运行 `/LTCG:PGINSTRUMENT`，重做所有测试，并运行 `/LTCG:PGOPTIMIZE`。

如果已使用 `/LTCG:PGOPTIMIZE` ，此警告将替换为一个错误。
