---
description: 了解详细信息：严重错误 C1047
title: 错误 C1047
ms.date: 11/04/2016
f1_keywords:
- C1047
helpviewer_keywords:
- C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
ms.openlocfilehash: e3aa85fb777850ce6ee754ee89b9e351b5eba975
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341186"
---
# <a name="fatal-error-c1047"></a>错误 C1047

对象或库文件“file”是使用比创建其他对象所用编译器旧的编译器创建的；请重新生成旧的对象和库

当使用 **/LTCG** 生成的对象文件或库链接在一起，而这些对象文件或库是用不同版本的 Visual C++ 工具集生成的，则会导致 C1047。

当你开始使用新版本的编译器，而不完全重新生成现有对象文件或库时，可能出现这种情况。

若要解决 C1047，请重新生成所有对象文件或库。
