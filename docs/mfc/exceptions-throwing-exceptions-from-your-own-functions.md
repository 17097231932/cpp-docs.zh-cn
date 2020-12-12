---
description: 了解详细信息：异常：从您自己的函数引发异常
title: 异常：从您自己的函数引发异常
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], from functions
- functions [MFC], throwing exceptions
- exceptions [MFC], throwing
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
ms.openlocfilehash: 5a9d789680eeba218370471b1259c8c664f3c3cd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290461"
---
# <a name="exceptions-throwing-exceptions-from-your-own-functions"></a>异常：从您自己的函数引发异常

可以单独使用 MFC 异常处理范例来捕获 MFC 或其他库中的函数引发的异常。 除了捕获库代码引发的异常之外，当您编写可能遇到异常条件的函数时，您还可以从自己的函数引发异常。

当引发异常时，将停止当前函数的执行并直接跳到最 **`catch`** 内部异常帧的块。 异常机制将绕过函数的正常退出路径。 因此，您必须确保在正常退出会删除那些内存块。

#### <a name="to-throw-an-exception"></a>引发异常

1. 使用 MFC 帮助程序函数之一，如 `AfxThrowMemoryException`。 这些函数引发适当类型的预分配异常对象。

   在以下示例中，函数将尝试分配两个内存块，并在任一分配失败时引发异常：

   [!code-cpp[NVC_MFCExceptions#17](codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]

   如果第一个分配失败，您可以只引发内存异常。 如果第一个分配成功，但第二个分配失败，则必须在引发异常之前释放第一次分配的块。 如果两个分配都成功，您可以正常地继续，并在退出函数时释放这些块。

     - 或 -

1. 使用用户定义的异常指示问题情况。 您可以引发任何类型的项，甚至引发整个类作为您的异常。

   以下示例尝试通过波形设备播放声音，并在失败时引发异常。

   [!code-cpp[NVC_MFCExceptions#18](codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]

> [!NOTE]
> MFC 的默认异常处理仅适用于指向 `CException` 对象（和 `CException` 派生类的对象）的指针。 上面的例子将绕过 MFC 的异常机制。

## <a name="see-also"></a>请参阅

[异常处理](exception-handling-in-mfc.md)
