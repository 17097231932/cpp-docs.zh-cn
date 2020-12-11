---
description: 了解详细信息： CD2DSolidColorBrush 类
title: CD2DSolidColorBrush 类
ms.date: 03/27/2019
f1_keywords:
- CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::Attach
- AFXRENDERTARGET/CD2DSolidColorBrush::Create
- AFXRENDERTARGET/CD2DSolidColorBrush::Destroy
- AFXRENDERTARGET/CD2DSolidColorBrush::Detach
- AFXRENDERTARGET/CD2DSolidColorBrush::Get
- AFXRENDERTARGET/CD2DSolidColorBrush::GetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::SetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::m_colorSolid
- AFXRENDERTARGET/CD2DSolidColorBrush::m_pSolidColorBrush
helpviewer_keywords:
- CD2DSolidColorBrush [MFC], CD2DSolidColorBrush
- CD2DSolidColorBrush [MFC], Attach
- CD2DSolidColorBrush [MFC], Create
- CD2DSolidColorBrush [MFC], Destroy
- CD2DSolidColorBrush [MFC], Detach
- CD2DSolidColorBrush [MFC], Get
- CD2DSolidColorBrush [MFC], GetColor
- CD2DSolidColorBrush [MFC], SetColor
- CD2DSolidColorBrush [MFC], m_colorSolid
- CD2DSolidColorBrush [MFC], m_pSolidColorBrush
ms.assetid: d4506637-acce-4f74-8a9b-f0a45571a735
ms.openlocfilehash: 57df3732a3c4239af6d9121426aa272c6f58417d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154599"
---
# <a name="cd2dsolidcolorbrush-class"></a>CD2DSolidColorBrush 类

ID2D1SolidColorBrush 的包装器。

## <a name="syntax"></a>语法

```
class CD2DSolidColorBrush : public CD2DBrush;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[CD2DSolidColorBrush：： CD2DSolidColorBrush](#cd2dsolidcolorbrush)|已重载。 构造 CD2DSolidColorBrush 对象。|
|[CD2DSolidColorBrush：： ~ CD2DSolidColorBrush](#_dtorcd2dsolidcolorbrush)|析构函数。 当正在销毁 D2D 纯色画笔对象时调用。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CD2DSolidColorBrush：： Attach](#attach)|将现有资源接口附加到对象|
|[CD2DSolidColorBrush：： Create](#create)|创建 CD2DSolidColorBrush。  (重写 [CD2DResource：： Create](../../mfc/reference/cd2dresource-class.md#create). ) |
|[CD2DSolidColorBrush：:D estroy](#destroy)|销毁 CD2DSolidColorBrush 对象。  (重写 [CD2DBrush：:D estroy](../../mfc/reference/cd2dbrush-class.md#destroy)。 ) |
|[CD2DSolidColorBrush：:D etach](#detach)|从对象分离资源接口|
|[CD2DSolidColorBrush：： Get](#get)|返回 ID2D1SolidColorBrush 接口|
|[CD2DSolidColorBrush：： GetColor](#getcolor)|检索纯色画笔的颜色|
|[CD2DSolidColorBrush：： SetColor](#setcolor)|指定此纯色画笔的颜色|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CD2DSolidColorBrush：： operator ID2D1SolidColorBrush *](#operator_id2d1solidcolorbrush_star)|返回 ID2D1SolidColorBrush 接口|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|描述|
|----------|-----------------|
|[CD2DSolidColorBrush：： m_colorSolid](#m_colorsolid)|画笔纯色。|
|[CD2DSolidColorBrush：： m_pSolidColorBrush](#m_psolidcolorbrush)|存储指向 ID2D1SolidColorBrush 对象的指针。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DSolidColorBrush](../../mfc/reference/cd2dsolidcolorbrush-class.md)

## <a name="requirements"></a>要求

**标头：** afxrendertarget

## <a name="cd2dsolidcolorbrushcd2dsolidcolorbrush"></a><a name="_dtorcd2dsolidcolorbrush"></a> CD2DSolidColorBrush：： ~ CD2DSolidColorBrush

析构函数。 当正在销毁 D2D 纯色画笔对象时调用。

```
virtual ~CD2DSolidColorBrush();
```

## <a name="cd2dsolidcolorbrushattach"></a><a name="attach"></a> CD2DSolidColorBrush：： Attach

将现有资源接口附加到对象

```cpp
void Attach(ID2D1SolidColorBrush* pResource);
```

### <a name="parameters"></a>parameters

*pResource*<br/>
现有的资源接口。 不能为 NULL

## <a name="cd2dsolidcolorbrushcd2dsolidcolorbrush"></a><a name="cd2dsolidcolorbrush"></a> CD2DSolidColorBrush：： CD2DSolidColorBrush

构造 CD2DSolidColorBrush 对象。

```
CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,
    D2D1_COLOR_F color,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,
    COLORREF color,
    int nAlpha = 255,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>parameters

*pParentTarget*<br/>
指向呈现器目标的指针。

*color*<br/>
画笔颜色的红色、绿色、蓝色和 alpha 值。

*pBrushProperties*<br/>
指向画笔的不透明度和转换的指针。

*bAutoDestroy*<br/>
指示对象将被所有者 (pParentTarget) 销毁。

*nAlpha*<br/>
画笔颜色的不透明度。

## <a name="cd2dsolidcolorbrushcreate"></a><a name="create"></a> CD2DSolidColorBrush：： Create

创建 CD2DSolidColorBrush。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>parameters

*pRenderTarget*<br/>
指向呈现器目标的指针。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回 HRESULT 错误代码。

## <a name="cd2dsolidcolorbrushdestroy"></a><a name="destroy"></a> CD2DSolidColorBrush：:D estroy

销毁 CD2DSolidColorBrush 对象。

```
virtual void Destroy();
```

## <a name="cd2dsolidcolorbrushdetach"></a><a name="detach"></a> CD2DSolidColorBrush：:D etach

从对象分离资源接口

```
ID2D1SolidColorBrush* Detach();
```

### <a name="return-value"></a>返回值

指向已分离资源接口的指针。

## <a name="cd2dsolidcolorbrushget"></a><a name="get"></a> CD2DSolidColorBrush：： Get

返回 ID2D1SolidColorBrush 接口

```
ID2D1SolidColorBrush* Get();
```

### <a name="return-value"></a>返回值

指向 ID2D1SolidColorBrush 接口的指针; 如果对象尚未初始化，则为 NULL。

## <a name="cd2dsolidcolorbrushgetcolor"></a><a name="getcolor"></a> CD2DSolidColorBrush：： GetColor

检索纯色画笔的颜色

```
D2D1_COLOR_F GetColor() const;
```

### <a name="return-value"></a>返回值

此纯色画笔的颜色

## <a name="cd2dsolidcolorbrushm_colorsolid"></a><a name="m_colorsolid"></a> CD2DSolidColorBrush：： m_colorSolid

画笔纯色。

```
D2D1_COLOR_F m_colorSolid;
```

## <a name="cd2dsolidcolorbrushm_psolidcolorbrush"></a><a name="m_psolidcolorbrush"></a> CD2DSolidColorBrush：： m_pSolidColorBrush

存储指向 ID2D1SolidColorBrush 对象的指针。

```
ID2D1SolidColorBrush* m_pSolidColorBrush;
```

## <a name="cd2dsolidcolorbrushoperator-id2d1solidcolorbrush"></a><a name="operator_id2d1solidcolorbrush_star"></a> CD2DSolidColorBrush：： operator ID2D1SolidColorBrush *

返回 ID2D1SolidColorBrush 接口

```
operator ID2D1SolidColorBrush*();
```

### <a name="return-value"></a>返回值

指向 ID2D1SolidColorBrush 接口的指针; 如果对象尚未初始化，则为 NULL。

## <a name="cd2dsolidcolorbrushsetcolor"></a><a name="setcolor"></a> CD2DSolidColorBrush：： SetColor

指定此纯色画笔的颜色

```cpp
void SetColor(D2D1_COLOR_F color);
```

### <a name="parameters"></a>parameters

*color*<br/>
此纯色画笔的颜色

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
