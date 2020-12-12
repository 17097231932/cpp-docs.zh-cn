---
description: 了解详细信息： COM 映射宏
title: COM 映射宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_COM_MAP
- atlcom/ATL::END_COM_MAP
helpviewer_keywords:
- COM interfaces, COM map macros
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
ms.openlocfilehash: 076a13418a48147654862c2b5a26688b195d5252
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141318"
---
# <a name="com-map-macros"></a>COM 映射宏

这些宏定义 COM 接口映射。

|宏|描述|
|-|-|
|[BEGIN_COM_MAP](#begin_com_map)|标记 COM 接口映射项的开头。|
|[END_COM_MAP](#end_com_map)|标记 COM 接口映射项的结尾。|

## <a name="requirements"></a>要求

**标头：** atlcom。h

## <a name="begin_com_map"></a><a name="begin_com_map"></a> BEGIN_COM_MAP

COM 映射是通过将对象上的接口公开给客户端的机制 `QueryInterface` 。

```
BEGIN_COM_MAP(x)
```

### <a name="parameters"></a>parameters

*x*<br/>
中正在公开其接口的类对象的名称。

### <a name="remarks"></a>备注

[CComObjectRootEx：： InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) 仅返回 COM 映射中接口的指针。 通过 BEGIN_COM_MAP 宏启动您的接口映射，为每个接口添加包含 [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) 宏或它的一个变量的条目，然后用 [END_COM_MAP](#end_com_map) 宏完成映射。

### <a name="example"></a>示例

从 ATL [BEEPER](../../overview/visual-cpp-samples.md) 示例：

[!code-cpp[NVC_ATL_COM#1](../../atl/codesnippet/cpp/com-map-macros_1.h)]

## <a name="end_com_map"></a><a name="end_com_map"></a> END_COM_MAP

结束 COM 接口映射的定义。

```
END_COM_MAP()
```

## <a name="see-also"></a>请参阅

[宏](../../atl/reference/atl-macros.md)<br/>
[COM 映射全局函数](../../atl/reference/com-map-global-functions.md)
