---
description: 了解详细信息： CRichEditCntrItem 类
title: CRichEditCntrItem 类
ms.date: 11/04/2016
f1_keywords:
- CRichEditCntrItem
- AFXRICH/CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::SyncToRichEditObject
helpviewer_keywords:
- CRichEditCntrItem [MFC], CRichEditCntrItem
- CRichEditCntrItem [MFC], SyncToRichEditObject
ms.assetid: 6c0b4efe-0fb8-4621-b5e1-fdcb8ec48c3b
ms.openlocfilehash: 9e65e70a3fb03b65ebf9af7a619a5c4fbd3dba32
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342955"
---
# <a name="cricheditcntritem-class"></a>CRichEditCntrItem 类

对于 [CRichEditView](../../mfc/reference/cricheditview-class.md) 和 [CRICHEDITDOC](../../mfc/reference/cricheditdoc-class.md)，提供 MFC 文档视图体系结构上下文中 rich edit 控件的功能。

## <a name="syntax"></a>语法

```
class CRichEditCntrItem : public COleClientItem
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[CRichEditCntrItem：： CRichEditCntrItem](#cricheditcntritem)|构造 `CRichEditCntrItem` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CRichEditCntrItem：： SyncToRichEditObject](#synctoricheditobject)|激活项作为另一种类型。|

## <a name="remarks"></a>备注

"Rich edit 控件" 是用户可在其中输入和编辑文本的窗口。 可以为文本分配字符和段落格式，还可以包括嵌入的 OLE 对象。 Rich edit 控件提供了用于设置文本格式的编程接口。 但是，应用程序必须实现使用户可进行格式设置操作所需的任何用户界面组件。

`CRichEditView` 保留文本及其格式特征。 `CRichEditDoc` 维护视图中的 OLE 客户端项的列表。 `CRichEditCntrItem` 提供对 OLE 客户端项的容器端访问。

这种 Windows 公共控制 (，因此， [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) 和相关类) 仅适用于在 windows 95/98 和 windows NT 版本3.51 及更高版本下运行的程序。

有关在 MFC 应用程序中使用 rich edit 容器项的示例，请参阅 [写字板](../../overview/visual-cpp-samples.md) 示例应用程序。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`CRichEditCntrItem`

## <a name="requirements"></a>要求

**标头：** afxrich

## <a name="cricheditcntritemcricheditcntritem"></a><a name="cricheditcntritem"></a> CRichEditCntrItem：： CRichEditCntrItem

调用此函数可创建 `CRichEditCntrItem` 对象并将其添加到容器文档中。

```
CRichEditCntrItem(
    REOBJECT* preo = NULL,
    CRichEditDoc* pContainer = NULL);
```

### <a name="parameters"></a>parameters

*preo*<br/>
指向描述 OLE 项的 [REOBJECT](/windows/win32/api/richole/ns-richole-reobject) 结构的指针。 `CRichEditCntrItem`围绕此 OLE 项构造新的对象。 如果 *preo* 为 NULL，则客户端项为空。

*pContainer*<br/>
指向将包含此项的容器文档的指针。 如果 *允许 pcontainer* 为 NULL，则必须显式调用 [COleDocument：： AddItem](../../mfc/reference/coledocument-class.md#additem) 将此客户端项添加到文档中。

### <a name="remarks"></a>备注

此函数不执行任何 OLE 初始化。

有关详细信息，请参阅 Windows SDK 中的 [REOBJECT](/windows/win32/api/richole/ns-richole-reobject) 结构。

## <a name="cricheditcntritemsynctoricheditobject"></a><a name="synctoricheditobject"></a> CRichEditCntrItem：： SyncToRichEditObject

调用此函数可将此的设备方面 [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect)同步 `CRichEditCntrltem` 到 *reo* 指定的。

```cpp
void SyncToRichEditObject(REOBJECT& reo);
```

### <a name="parameters"></a>parameters

*reo*<br/>
对描述 OLE 项的 [REOBJECT](/windows/win32/api/richole/ns-richole-reobject) 结构的引用。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的 [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect) 。

## <a name="see-also"></a>请参阅

[MFC 示例写字板](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem 类](../../mfc/reference/coleclientitem-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc 类](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditView 类](../../mfc/reference/cricheditview-class.md)
