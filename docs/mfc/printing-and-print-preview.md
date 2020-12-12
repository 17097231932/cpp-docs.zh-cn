---
description: 了解详细信息：打印和打印预览
title: 打印和打印预览
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC]
- previewing printing
- printing [MFC]
- print preview
- printing [MFC], print preview
ms.assetid: d15059cd-32de-4450-95f7-e73aece238f6
ms.openlocfilehash: 57dfd8eed1719b17f776a62273c9afa9ff5e80f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205832"
---
# <a name="printing-and-print-preview"></a>打印和打印预览

MFC 支持通过类 [CView](reference/cview-class.md)的程序文档的打印和打印预览。 对于基本打印和打印预览，只需重写视图类的 [OnDraw](reference/cview-class.md#ondraw) 成员函数（您必须执行此操作）。 该函数可以绘制到屏幕上的视图、实际打印机的打印机设备上下文或在屏幕上模拟打印机的设备上下文。

你还可以添加代码以管理多页文档打印和预览，对打印的文档进行分页并向其添加页眉和页脚。

本系列文章介绍了如何在 Microsoft 基础类库 (MFC) 实现打印，以及如何利用已内置到框架中的打印体系结构。 本文还介绍了 MFC 如何支持轻松实现打印预览功能，以及如何使用和修改该功能。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [打印](printing.md)

- [打印预览体系结构](print-preview-architecture.md)

- [示例](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>请参阅

[用户界面元素](user-interface-elements-mfc.md)
