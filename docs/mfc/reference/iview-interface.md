---
title: IView 接口
ms.date: 11/04/2016
f1_keywords:
- IView
- AFXWINFORMS/IView
- AFXWINFORMS/IView::OnActivateView
- AFXWINFORMS/IView::OnInitialUpdate
- AFXWINFORMS/IView::OnUpdate
helpviewer_keywords:
- views [MFC]
- IView class [MFC]
- views [MFC], classes
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
ms.openlocfilehash: 9233ee5a8330c4b2c79ebc7b79e0616612c00204
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743420"
---
# <a name="iview-interface"></a>IView 接口

实现多种方法， [CWinFormsView](../../mfc/reference/cwinformsview-class.md) 使用这些方法将视图通知发送到托管控件。

## <a name="syntax"></a>语法

```
interface class IView
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[IView：： OnActivateView](#onactivateview)|当激活或停用视图时，由 MFC 调用。|
|[IView：： OnInitialUpdate](#oninitialupdate)|在视图第一次附加到文档之后但最初显示视图之前由框架调用。|
|[IView：： OnUpdate](#onupdate)|在视图的文档被修改后由 MFC 调用;此函数允许视图更新其显示以反映修改。|

### <a name="remarks"></a>备注

`IView` 实现多种方法，这些方法 `CWinFormsView` 使用将常见视图通知转发到托管托管控件。 这些是 [OnInitialUpdate](#oninitialupdate)、 [OnUpdate](#onupdate) 和 [OnActivateView](#onactivateview)。

`IView` 类似于 [CView](../../mfc/reference/cview-class.md)，但仅用于托管视图和控件。

有关使用 Windows 窗体的详细信息，请参阅 [在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="requirements"></a>要求

标头：afxwinforms.h（在程序集 atlmfc\lib\mfcmifc80.dll 中定义）

## <a name="iviewonactivateview"></a><a name="onactivateview"></a> IView：： OnActivateView

当激活或停用视图时，由 MFC 调用。

```cpp
void OnActivateView(bool activate);
```

## <a name="parameters"></a>参数

*激活*<br/>
指示是否正在激活或停用视图。

## <a name="iviewoninitialupdate"></a><a name="oninitialupdate"></a> IView：： OnInitialUpdate

在视图第一次附加到文档之后但最初显示视图之前由框架调用。

```cpp
void OnInitialUpdate();
```

## <a name="iviewonupdate"></a><a name="onupdate"></a> IView：： OnUpdate

在视图的文档被修改后由 MFC 调用。

```cpp
void OnUpdate();
```

### <a name="remarks"></a>备注

此函数允许视图更新其显示以反映修改。

## <a name="see-also"></a>请参阅

[CWinFormsView 类](../../mfc/reference/cwinformsview-class.md)<br/>
[CView 类](../../mfc/reference/cview-class.md)
