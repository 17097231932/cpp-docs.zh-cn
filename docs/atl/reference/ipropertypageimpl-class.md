---
description: 了解详细信息： IPropertyPageImpl 类
title: IPropertyPageImpl 类
ms.date: 11/04/2016
f1_keywords:
- IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::Activate
- ATLCTL/ATL::IPropertyPageImpl::Apply
- ATLCTL/ATL::IPropertyPageImpl::Deactivate
- ATLCTL/ATL::IPropertyPageImpl::GetPageInfo
- ATLCTL/ATL::IPropertyPageImpl::Help
- ATLCTL/ATL::IPropertyPageImpl::IsPageDirty
- ATLCTL/ATL::IPropertyPageImpl::Move
- ATLCTL/ATL::IPropertyPageImpl::SetDirty
- ATLCTL/ATL::IPropertyPageImpl::SetObjects
- ATLCTL/ATL::IPropertyPageImpl::SetPageSite
- ATLCTL/ATL::IPropertyPageImpl::Show
- ATLCTL/ATL::IPropertyPageImpl::TranslateAccelerator
- ATLCTL/ATL::IPropertyPageImpl::m_bDirty
- ATLCTL/ATL::IPropertyPageImpl::m_dwDocString
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpContext
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpFile
- ATLCTL/ATL::IPropertyPageImpl::m_dwTitle
- ATLCTL/ATL::IPropertyPageImpl::m_nObjects
- ATLCTL/ATL::IPropertyPageImpl::m_pPageSite
- ATLCTL/ATL::IPropertyPageImpl::m_ppUnk
- ATLCTL/ATL::IPropertyPageImpl::m_size
helpviewer_keywords:
- property pages
- IPropertyPage ATL implementation
- IPropertyPageImpl class
ms.assetid: f9b7c8b1-7a04-4eab-aa63-63efddb740fa
ms.openlocfilehash: c3b8a52d3aff0beeb175a18af56a207284ff538d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158135"
---
# <a name="ipropertypageimpl-class"></a>IPropertyPageImpl 类

此类实现 `IUnknown` 并提供 [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) 接口的默认实现。

> [!IMPORTANT]
> 此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template<class T>
class IPropertyPageImpl
```

#### <a name="parameters"></a>parameters

*T*<br/>
派生自的类 `IPropertyPageImpl` 。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[IPropertyPageImpl::IPropertyPageImpl](#ipropertypageimpl)|构造函数。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[IPropertyPageImpl：： Activate](#activate)|为属性页创建对话框窗口。|
|[IPropertyPageImpl：： Apply](#apply)|将当前属性页值应用到通过指定的基础对象 `SetObjects` 。 ATL 实现返回 S_OK。|
|[IPropertyPageImpl：:D eactivate](#deactivate)|销毁用创建的窗口 `Activate` 。|
|[IPropertyPageImpl::GetPageInfo](#getpageinfo)|检索有关属性页的信息。|
|[IPropertyPageImpl：： Help](#help)|调用属性页的 Windows 帮助。|
|[IPropertyPageImpl::IsPageDirty](#ispagedirty)|指示属性页在激活后是否已更改。|
|[IPropertyPageImpl：： Move](#move)|定位属性页对话框并调整其大小。|
|[IPropertyPageImpl::SetDirty](#setdirty)|将属性页的状态标记为 "已更改" 或 "未更改"。|
|[IPropertyPageImpl::SetObjects](#setobjects)|提供 `IUnknown` 与属性页关联的对象的指针数组。 这些对象通过调用来接收当前属性页值 `Apply` 。|
|[IPropertyPageImpl::SetPageSite](#setpagesite)|为属性页提供一个 `IPropertyPageSite` 指针，属性页通过该指针与属性框进行通信。|
|[IPropertyPageImpl：： Show](#show)|使 "属性页" 对话框可见或不可见。|
|[IPropertyPageImpl：： TranslateAccelerator](#translateaccelerator)|处理指定的击键。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[IPropertyPageImpl：： m_bDirty](#m_bdirty)|指定属性页的状态是否已更改。|
|[IPropertyPageImpl：： m_dwDocString](#m_dwdocstring)|存储与说明属性页的文本字符串相关联的资源标识符。|
|[IPropertyPageImpl：： m_dwHelpContext](#m_dwhelpcontext)|存储与属性页关联的帮助主题的上下文标识符。|
|[IPropertyPageImpl：： m_dwHelpFile](#m_dwhelpfile)|存储与说明属性页的帮助文件的名称关联的资源标识符。|
|[IPropertyPageImpl：： m_dwTitle](#m_dwtitle)|存储与显示在属性页的选项卡中的文本字符串相关联的资源标识符。|
|[IPropertyPageImpl：： m_nObjects](#m_nobjects)|存储与属性页关联的对象的数目。|
|[IPropertyPageImpl：： m_pPageSite](#m_ppagesite)|指向 `IPropertyPageSite` 属性页与属性框通信时所使用的接口。|
|[IPropertyPageImpl：： m_ppUnk](#m_ppunk)|指向 `IUnknown` 与属性页关联的对象的指针数组。|
|[IPropertyPageImpl：： m_size](#m_size)|存储属性页对话框的高度和宽度（以像素为单位）。|

## <a name="remarks"></a>备注

[IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage)接口允许对象管理属性表中的特定属性页。 类 `IPropertyPageImpl` 提供此接口的默认实现，并 `IUnknown` 通过在调试版本中将信息发送到转储设备来实现。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)， [创建 atl 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IPropertyPage`

`IPropertyPageImpl`

## <a name="requirements"></a>要求

**标头：** atlctl

## <a name="ipropertypageimplactivate"></a><a name="activate"></a> IPropertyPageImpl：： Activate

为属性页创建对话框窗口。

```
HRESULT Activate(
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```

### <a name="remarks"></a>备注

默认情况下，无论 *bModal* 参数的值是什么，对话框始终都是无模式的。

请参阅 Windows SDK 中的 [IPropertyPage：： Activate](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-activate) 。

## <a name="ipropertypageimplapply"></a><a name="apply"></a> IPropertyPageImpl：： Apply

将当前属性页值应用到通过指定的基础对象 `SetObjects` 。

```
HRESULT Apply();
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的 [IPropertyPage：： Apply](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-apply) 。

## <a name="ipropertypageimpldeactivate"></a><a name="deactivate"></a> IPropertyPageImpl：:D eactivate

销毁用 [Activate](#activate)创建的对话框窗口。

```
HRESULT Deactivate();
```

### <a name="remarks"></a>备注

请参阅 IPropertyPage： Windows SDK 中的 [：:D eactivate](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-deactivate) 。

## <a name="ipropertypageimplgetpageinfo"></a><a name="getpageinfo"></a> IPropertyPageImpl::GetPageInfo

用数据成员中包含的信息填充 *pPageInfo* 结构。

```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>备注

`GetPageInfo` 加载与 [m_dwDocString](#m_dwdocstring)、 [m_dwHelpFile](#m_dwhelpfile)和 [m_dwTitle](#m_dwtitle)关联的字符串资源。

请参阅 Windows SDK 中的 [IPropertyPage：： GetPageInfo](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-getpageinfo) 。

## <a name="ipropertypageimplhelp"></a><a name="help"></a> IPropertyPageImpl：： Help

调用属性页的 Windows 帮助。

```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的 [IPropertyPage：： Help](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-help) 。

## <a name="ipropertypageimplipropertypageimpl"></a><a name="ipropertypageimpl"></a> IPropertyPageImpl::IPropertyPageImpl

构造函数。

```
IPropertyPageImpl();
```

### <a name="remarks"></a>备注

初始化所有数据成员。

## <a name="ipropertypageimplispagedirty"></a><a name="ispagedirty"></a> IPropertyPageImpl::IsPageDirty

指示属性页在激活后是否已更改。

```
HRESULT IsPageDirty(void);
```

### <a name="remarks"></a>备注

`IsPageDirty` 如果页面自激活后发生了更改，则返回 S_OK。

## <a name="ipropertypageimplm_bdirty"></a><a name="m_bdirty"></a> IPropertyPageImpl：： m_bDirty

指定属性页的状态是否已更改。

```
BOOL m_bDirty;
```

## <a name="ipropertypageimplm_nobjects"></a><a name="m_nobjects"></a> IPropertyPageImpl：： m_nObjects

存储与属性页关联的对象的数目。

```
ULONG m_nObjects;
```

## <a name="ipropertypageimplm_dwhelpcontext"></a><a name="m_dwhelpcontext"></a> IPropertyPageImpl：： m_dwHelpContext

存储与属性页关联的帮助主题的上下文标识符。

```
DWORD m_dwHelpContext;
```

## <a name="ipropertypageimplm_dwdocstring"></a><a name="m_dwdocstring"></a> IPropertyPageImpl：： m_dwDocString

存储与说明属性页的文本字符串相关联的资源标识符。

```
UINT m_dwDocString;
```

## <a name="ipropertypageimplm_dwhelpfile"></a><a name="m_dwhelpfile"></a> IPropertyPageImpl：： m_dwHelpFile

存储与说明属性页的帮助文件的名称关联的资源标识符。

```
UINT m_dwHelpFile;
```

## <a name="ipropertypageimplm_dwtitle"></a><a name="m_dwtitle"></a> IPropertyPageImpl：： m_dwTitle

存储与显示在属性页的选项卡中的文本字符串相关联的资源标识符。

```
UINT m_dwTitle;
```

## <a name="ipropertypageimplm_ppagesite"></a><a name="m_ppagesite"></a> IPropertyPageImpl：： m_pPageSite

指向 [IPropertyPageSite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) 接口，通过该接口，属性页与属性框通信。

```
IPropertyPageSite* m_pPageSite;
```

## <a name="ipropertypageimplm_ppunk"></a><a name="m_ppunk"></a> IPropertyPageImpl：： m_ppUnk

指向 `IUnknown` 与属性页关联的对象的指针数组。

```
IUnknown** m_ppUnk;
```

## <a name="ipropertypageimplm_size"></a><a name="m_size"></a> IPropertyPageImpl：： m_size

存储属性页对话框的高度和宽度（以像素为单位）。

```
SIZE m_size;
```

## <a name="ipropertypageimplmove"></a><a name="move"></a> IPropertyPageImpl：： Move

定位属性页对话框并调整其大小。

```
HRESULT Move(LPCRECT pRect);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的 [IPropertyPage：： Move](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-move) 。

## <a name="ipropertypageimplsetdirty"></a><a name="setdirty"></a> IPropertyPageImpl::SetDirty

根据 *bDirty* 的值，将属性页的状态标记为 "已更改" 或 "未更改"。

```cpp
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>parameters

*bDirty*<br/>
中如果为 TRUE，则属性页的状态将标记为已更改。 否则，会将其标记为未更改。

### <a name="remarks"></a>备注

如有必要， `SetDirty` 通知帧属性页面已更改。

## <a name="ipropertypageimplsetobjects"></a><a name="setobjects"></a> IPropertyPageImpl::SetObjects

提供 `IUnknown` 与属性页关联的对象的指针数组。

```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的 [IPropertyPage：： SetObjects](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setobjects) 。

## <a name="ipropertypageimplsetpagesite"></a><a name="setpagesite"></a> IPropertyPageImpl::SetPageSite

提供具有 [IPropertyPageSite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) 指针的属性页，属性页通过该指针与属性框进行通信。

```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的 [IPropertyPage：： SetPageSite](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setpagesite) 。

## <a name="ipropertypageimplshow"></a><a name="show"></a> IPropertyPageImpl：： Show

使 "属性页" 对话框可见或不可见。

```
HRESULT Show(UINT nCmdShow);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的 [IPropertyPage：： Show](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-show) 。

## <a name="ipropertypageimpltranslateaccelerator"></a><a name="translateaccelerator"></a> IPropertyPageImpl：： TranslateAccelerator

处理在中指定的击键 `pMsg` 。

```
HRESULT TranslateAccelerator(MSG* pMsg);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的 [IPropertyPage：： TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-translateaccelerator) 。

## <a name="see-also"></a>请参阅

[IPropertyPage2Impl 类](../../atl/reference/ipropertypage2impl-class.md)<br/>
[IPerPropertyBrowsingImpl 类](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl 类](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
