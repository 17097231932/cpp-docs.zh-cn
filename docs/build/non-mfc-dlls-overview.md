---
description: 详细了解：非 MFC DLL：概述
title: 非 MFC DLL：概述
ms.date: 11/04/2016
helpviewer_keywords:
- non-MFC DLLs [C++]
- DLLs [C++], non-MFC
ms.assetid: 1ed5d1ee-e20c-47d7-801d-87ea26a73842
ms.openlocfilehash: 2b71653be8a665684b7e79dcb48ac54d86834be0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179832"
---
# <a name="non-mfc-dlls-overview"></a>非 MFC DLL：概述

非 MFC DLL 是不在内部使用 MFC 的 DLL，DLL 中的导出函数可以由 MFC 或非 MFC 可执行文件调用。 通常使用标准 C 接口从非 MFC DLL 导出函数。

有关非 MFC DLL 的详细信息，请参阅 Windows SDK 中的[动态链接库](/windows/win32/dlls/dynamic-link-libraries)。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [演练：创建和使用动态链接库](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)

- [从 DLL 导出](exporting-from-a-dll.md)

- [将可执行文件链接到 DLL](linking-an-executable-to-a-dll.md)

- [初始化 DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [静态链接到 MFC 的规则 MFC DLL](regular-dlls-statically-linked-to-mfc.md)

- [动态链接到 MFC 的规则 MFC DLL](regular-dlls-dynamically-linked-to-mfc.md)

- [MFC 扩展 DLL：概述](extension-dlls-overview.md)

## <a name="see-also"></a>请参阅

[DLL 的类型](kinds-of-dlls.md)
