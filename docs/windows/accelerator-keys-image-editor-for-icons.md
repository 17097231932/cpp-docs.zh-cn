---
description: '了解详细信息：快捷键 (c + + 图像编辑器) '
title: '用于图标 (c + + 图像编辑器的快捷键) '
ms.date: 02/15/2019
helpviewer_keywords:
- accelerator keys
- Image editor [C++], accelerator keys
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
ms.openlocfilehash: 74062789a7fc6ff6b3b15364d1379861f7bea1c6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280282"
---
# <a name="accelerator-keys-c-image-editor-for-icons"></a>用于图标 (c + + 图像编辑器的快捷键) 

下面是默认情况下绑定到密钥的图像编辑器命令的快捷键。 若要更改加速键，请转到 "菜单 **工具**  >  "**选项**，然后选择 "**环境**" 文件夹下的 "**键盘**"。 有关详细信息，请参阅[标识并自定义键盘快捷方式](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)。

> [!NOTE]
> 对话框中的可用选项以及显示的菜单命令的名称和位置可能与“帮助”中的描述不同，具体取决于您的当前设置或版本。 若要更改设置，请转到 "菜单" "**工具**" "  >  **导入和导出设置**"。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。

|命令|键|说明|
|-------------|----------|-----------------|
|AirBrushTool|Ctrl + A |使用具有选定大小和颜色的喷枪进行绘制。|
|图像.画笔工具|**Ctrl** + **B**|使用所选形状、大小和颜色绘制画笔。|
|CopyAndOutlineSelection|**Ctrl**  + **移位**  + **U**|创建当前选定内容的副本并绘制其轮廓。 如果当前选定内容中包含背景颜色，则在选择 [透明](./image-editor-for-icons.md) 效果时，将排除该背景色。|
|图像.不透明处理|**Ctrl** + **J**|使当前选定内容为不 [透明或透明](./image-editor-for-icons.md)。|
|图像.椭圆工具|**Ctrl**  + **P**|使用所选的线条宽度和颜色绘制椭圆。|
|EraserTool|**Ctrl**  + **移位**  + **I**|使用当前背景色)  (清除部分图像。|
|图像.实心椭圆工具|**Ctrl**  + **移位**  + **Alt**  + **P**|绘制一个实心椭圆。|
|图像.实心矩形工具|**Ctrl**  + **移位**  + **Alt**  + **R**|绘制一个实心矩形。|
|FilledRoundRectangleTool|**Ctrl**  + **移位**  + **Alt**  + **W**|绘制一个实心圆角矩形。|
|图像.填充工具| Ctrl +   F|填充一块区域。|
|图像.水平翻转| Ctrl +   H|水平翻转图像或选定内容。|
|图像.垂直翻转|**移位** + **Alt**  + **H**|垂直翻转图像或选定内容。|
|图像.较大画笔|**Ctrl** + **=**|增加画笔大小（每个方向上增加一个像素）。 若要减小画笔大小，请参见本表中的“图像.较小画笔”。|
|图像.直线工具|**Ctrl**  + **L**|用选定形状、大小和颜色绘制一条直线。|
|图像.放大工具|**Ctrl**  + **M**|激活 **放大** 工具，该工具允许您放大图像的特定部分。|
|图像.放大|Ctrl + Shift + M|在当前放大倍数和 1:1 放大倍数之间切换。|
|图像.新建图像类型|插入|启动 " [新建 \<Device> 图像类型" 对话框](./creating-an-icon-or-other-image-image-editor-for-icons.md) ，使用该对话框可以为不同图像类型创建图像。|
|图像.下一种颜色|**Ctrl**  + **]**<br /><br /> - 或 -<br /><br /> **Ctrl**  + **右箭头**|将绘制前景色更改为下一个调色板颜色。|
|Image.NextRightColor|**Ctrl**  + **移位**  + **]**<br /><br /> - 或 -<br /><br /> **移位**  + **Ctrl**  + **右箭头**|将绘制背景色更改为下一个调色板颜色。|
|图像.空心椭圆工具|**移位**  + **Alt**  + **P**|用一个轮廓绘制实心椭圆。|
|图像.空心矩形工具|**移位**  + **Alt**  + **R**|用一个轮廓绘制实心矩形|
|OutlinedRoundRectangleTool|**移位**  + **Alt**  + **W**|用一个轮廓绘制实心圆角矩形。|
|图像.铅笔工具|**Ctrl**  + **I**|使用单像素铅笔绘制。|
|图像.上一种颜色|**Ctrl**  + **[**<br /><br /> - 或 -<br /><br /> **Ctrl**  + **向左键**|将绘制前景色更改为以前的调色板颜色。|
|Image.PreviousRightColor|**Ctrl**  + **移位**  + **[**<br /><br /> - 或 -<br /><br /> **移位**  + **Ctrl**  + **向左键**|将绘制背景色更改为以前的调色板颜色。|
|图像.矩形选择工具|**移位**  + **Alt**  + **S**|选择要移动、复制或编辑的图像的矩形部分。|
|图像.矩形工具|ATL + R|使用所选的线条宽度和颜色绘制矩形。|
|图像.旋转 90 度| Ctrl +   Shift +   H|将图像或选定内容旋转 90 度。|
|图像.圆角矩形工具|**Alt**  + **W**|绘制具有选定线条宽度和颜色的圆角矩形。|
|图像.网格|**Ctrl**  + **Alt**  + **S**|切换像素网格 (选中或清除 "[网格设置" 对话框](./image-editor-for-icons.md)中的 "**像素网格**" 选项) 。|
|图像.显示平铺网格|**Ctrl**  + **移位**  + **Alt**  + **S**|切换磁贴网格 (选中或清除 "[网格设置" 对话框](./image-editor-for-icons.md)中的 "**磁贴网格**" 选项) 。|
|图像.小画笔|Ctrl + . （句点）|将 **画笔** 大小缩小为一个像素。 （请参见本表中的 Image.LargerBrush 和 Image.SmallerBrush。）|
|图像.较小画笔|  +  Ctrl **-** (减) |减小画笔大小（每个方向上减小一个像素）。 若要再次扩展画笔大小，请参见本表中的 Image.LargerBrush。|
|图像.文本工具| Ctrl  +  T |打开 " [文本工具" 对话框](./image-editor-for-icons.md)。|
|UseSelectionAsBrush|**Ctrl**  + **U**|将当前所选内容用作画笔来绘制。|
|图像.放大|**Ctrl**  + **移位**  + **.** （句点）<br /><br /> - 或 -<br /><br /> **Ctrl**  + **向上键**|增加当前视图的放大倍数。|
|图像.缩小|**Ctrl**  + **，** (逗号) <br /><br /> - 或 -<br /><br /> **Ctrl**  + **向下键**|减小当前视图的放大倍数。|

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[图标的图像编辑器](image-editor-for-icons.md)<br/>
[如何：创建图标或其他图像](creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[如何：编辑图像](selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[如何：使用绘图工具](using-a-drawing-tool-image-editor-for-icons.md)<br/>
[如何：使用颜色](working-with-color-image-editor-for-icons.md)<br/>
