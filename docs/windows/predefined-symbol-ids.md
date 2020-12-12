---
description: 了解详细信息：预定义的符号 Id
title: 预定义的符号 ID
ms.date: 02/14/2019
helpviewer_keywords:
- symbols [C++], predefined IDs
- predefined symbol IDs
ms.assetid: 91a5d610-1a04-47e8-b8a4-63ad650a90df
ms.openlocfilehash: f28f41b3194e65824b0c06285c0c4e73cfce8b39
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180027"
---
# <a name="predefined-symbol-ids"></a>预定义的符号 ID

开始新项目时，根据项目类型预定义了一些符号 ID 供你使用。 这些符号 ID 支持 MFC 等各种库和项目类型。 它们表示通常包含于任何应用程序或硬件项（如鼠标或打印机）动作中的常见任务。

处理资源时，这些符号 ID 变得很重要。 它们可在编辑快捷键对应表时使用，其中某些已与虚拟键关联。 还可以通过 [属性窗口](/visualstudio/ide/reference/properties-window)获取它们。 可以将任何预定义的符号 Id 分配给新资源，也可以为其分配快捷键，与符号 ID 关联的功能会自动与该键组合关联。

库具有预定义的符号，它们将显示为项目的一部分：

- [ATL 预定义符号](../windows/atl-predefined-symbols.md)

- [MFC 预定义符号](../windows/mfc-predefined-symbols.md)

- [Win32 预定义符号](../windows/win32-predefined-symbols.md)

> [!NOTE]
> 预定义的符号始终是只读的。

## <a name="requirements"></a>要求

Win32、MFC 或 ATL

## <a name="see-also"></a>请参阅

[ (符号的资源标识符) ](../windows/symbols-resource-identifiers.md)<br/>
[如何：创建符号](../windows/creating-new-symbols.md)<br/>
[如何：管理符号](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
