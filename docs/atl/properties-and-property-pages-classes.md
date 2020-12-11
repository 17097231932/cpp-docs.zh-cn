---
description: 了解更多：属性和属性页类
title: ATL) 的属性和属性页类 (
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- property pages, classes
- properties [ATL], classes
- properties [ATL]
ms.assetid: 31616f98-69f8-48b2-8d58-b8e7d1c2b2d8
ms.openlocfilehash: 1fddb9626afcab908ae6f7ffb085c263b7a84af7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159188"
---
# <a name="properties-and-property-pages-classes"></a>属性和属性页类

以下类支持属性和属性页：

- [CComDispatchDriver](../atl/reference/atl-typedefs.md#ccomdispatchdriver) 通过指针检索或设置对象的属性 `IDispatch` 。

- [CStockPropImpl](../atl/reference/cstockpropimpl-class.md) 实现 ATL 支持的常用属性。

- [IPerPropertyBrowsingImpl](../atl/reference/iperpropertybrowsingimpl-class.md) 访问对象的属性页中的信息。

- [IPersistPropertyBagImpl](../atl/reference/ipersistpropertybagimpl-class.md) 将对象的属性存储在客户端提供的属性包中。

- [IPropertyPageImpl](../atl/reference/ipropertypageimpl-class.md) 管理属性表中的特定属性页。

- [IPropertyPage2Impl](../atl/reference/ipropertypage2impl-class.md) 与类似 `IPropertyPageImpl` ，但还允许客户端选择属性页中的特定属性。

- [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md) 获取对象支持的属性页的 Clsid。

## <a name="related-articles"></a>相关文章

[ATL 教程](../atl/active-template-library-atl-tutorial.md)

[ATL COM 属性页](../atl/atl-com-property-pages.md)

## <a name="see-also"></a>请参阅

[类概述](../atl/atl-class-overview.md)<br/>
[属性映射宏](../atl/reference/property-map-macros.md)
