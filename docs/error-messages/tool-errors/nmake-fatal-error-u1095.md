---
description: 了解详细信息： NMAKE 错误 U1095
title: NMAKE 错误 U1095
ms.date: 11/04/2016
f1_keywords:
- U1095
helpviewer_keywords:
- U1095
ms.assetid: a392582b-06db-4568-9c13-450293a4fbda
ms.openlocfilehash: 047c4aaca15917b884a44bd1e3e156bf8825274f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345337"
---
# <a name="nmake-fatal-error-u1095"></a>NMAKE 错误 U1095

扩展的命令行 "命令行" 太长

宏展开后，给定的命令行超过了操作系统的命令行长度限制。

在命令行上，MS-DOS 允许最多128个字符。

如果命令适用于可接受文件中的命令行输入的程序，请更改命令，并从磁盘上的文件或内联文件提供输入。 例如，LINK 和 LIB 接受响应文件中的输入。
