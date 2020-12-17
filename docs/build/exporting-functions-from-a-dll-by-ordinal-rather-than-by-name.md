---
description: 详细了解：按序号而不是按名称从 DLL 导出函数
title: 按序号而不是按名称从 DLL 导出函数
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
ms.openlocfilehash: 84d200e2c37161d6bef3e64e72130204640088c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156497"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>按序号而不是按名称从 DLL 导出函数

从 DLL 导出函数的最简单方法是按名称导出函数。 在使用 `__declspec(dllexport)` 时（举个例子）会发生这种情况。 但可以改为按序号导出函数。 使用这种技术时，必须使用 .def 文件，而不是 `__declspec(dllexport)`。 若要指定函数的序号值，请在 .def 文件中将其序号追加到函数名称。 有关指定序号的信息，请参阅[使用 .def 文件从 DLL 导出](exporting-from-a-dll-using-def-files.md)。

> [!TIP]
> 如果要优化 DLL 的文件大小，请对每个导出函数使用 NONAME  特性。 通过 NONAME  特性，序号存储在 DLL 的导出表中，而不是函数名称中。 如果要导出许多函数，则这可能会节省很多。

## <a name="what-do-you-want-to-do"></a>你希望做什么？

- [使用 .def 文件以便可以按序号导出](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>请参阅

[从 DLL 导出](exporting-from-a-dll.md)
