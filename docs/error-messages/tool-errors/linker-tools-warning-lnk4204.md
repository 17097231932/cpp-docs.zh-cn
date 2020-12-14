---
description: 了解详细信息：链接器工具警告 LNK4204
title: 链接器工具警告 LNK4204
ms.date: 11/04/2016
f1_keywords:
- LNK4204
helpviewer_keywords:
- LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
ms.openlocfilehash: e0e61967a7b3bf42eb2c084d73c7c0aa9485c47e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294192"
---
# <a name="linker-tools-warning-lnk4204"></a>链接器工具警告 LNK4204

"filename" 缺少引用模块的调试信息;正在链接对象，如同没有调试信息一样

.Pdb 文件具有错误的签名。 链接器将继续链接对象，但不包含调试信息。 您可能想要使用 [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) 选项重新编译对象文件。

如果库中的某些对象指的是不再存在的文件，则可能会发生 LNK4204。 重新生成解决方案时可能会发生这种情况，例如，由于编译错误，对象文件可能会被删除，并且不会重新生成。 在这种情况下，请使用 **/Z7** 或 **/fd** 进行编译，以更新对象，使其引用每个库的单个文件 (不是默认 .pdb 文件名) 。  有关详细信息，请参阅 [/fd (程序数据库文件名) ](../../build/reference/fd-program-database-file-name.md)。  请确保在源代码管理系统中每次更新 .pdb 后，都将 .pdb 保存在库中。
