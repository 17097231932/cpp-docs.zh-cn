---
description: 详细了解：FreeLibrary 和 AfxFreeLibrary
title: FreeLibrary 和 AfxFreeLibrary
ms.date: 11/04/2016
f1_keywords:
- FreeLibrary
- AfxFreeLibrary
helpviewer_keywords:
- extension DLLs [C++], unloading
- AfxFreeLibrary method
- unloading DLLs
- FreeLibrary method
- DLLs [C++], linking
- explicit linking [C++]
- DLLs [C++], unloading
ms.assetid: 4a48d290-3971-43e9-8e97-ba656cd0c8f8
ms.openlocfilehash: ea4da8c69aa663add85e740d99b68731e263b442
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162789"
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary 和 AfxFreeLibrary

当不再需要 DLL 模块时，显式链接到 DLL 的进程会调用 [FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary) 函数。 此函数使模块的引用计数递减。 而且，如果引用计数为零，则从进程的地址空间取消映射。

在 MFC 应用程序中，请使用 [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary) 而非 `FreeLibrary` 来卸载 MFC 扩展 DLL。 `AfxFreeLibrary` 的接口（函数原型）与 `FreeLibrary` 相同。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [将可执行文件链接到 DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [将可执行文件链接到 DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？

- [LoadLibrary 和 AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>请参阅

[在 Visual Studio 中创建 C/C++ DLL](dlls-in-visual-cpp.md)\
[FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)\
[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)
