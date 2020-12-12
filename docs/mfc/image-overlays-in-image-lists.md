---
description: 了解详细信息：图像列表中的图像覆盖
title: 图像列表中的图像覆盖
ms.date: 11/04/2016
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
ms.openlocfilehash: dd65a27c9ef66311311195c1493e91be8c66d100
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290110"
---
# <a name="image-overlays-in-image-lists"></a>图像列表中的图像覆盖

 ([CImageList](reference/cimagelist-class.md)) 的每个图像列表都包含一个要用作覆盖屏蔽的图像列表。 “覆盖掩码”是在其他图像上透明绘制的图像。 任何图像都可用作覆盖掩码。 每个图像列表您最多可以指定 4 个覆盖掩码。

使用 [SetOverlayImage](reference/cimagelist-class.md#setoverlayimage) 成员函数、图像的索引和覆盖掩码的索引，将图像的索引添加到覆盖掩码列表。 请注意，覆盖掩码的索引是从 1 而不是 0 开始的。

使用对的单个调用，可以在图像上绘制覆盖屏蔽 `Draw` 。 参数包括要绘制图像的索引和覆盖掩码的索引。 必须使用 [INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask) 宏来指定覆盖掩码的索引。 在调用 [DrawIndirect](reference/cimagelist-class.md#drawindirect) 成员函数时，还可以指定覆盖图像。

## <a name="see-also"></a>请参阅

[使用 CImageList](using-cimagelist.md)<br/>
[控件](controls-mfc.md)
