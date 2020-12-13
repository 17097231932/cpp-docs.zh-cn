---
description: 了解有关： IUnknown 的详细信息
title: IUnknown
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
ms.openlocfilehash: ddfd35155162275885a1c0c842b4589fa6773a4a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152641"
---
# <a name="iunknown"></a>IUnknown

[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 是每个其他 COM 接口的基接口。  此接口定义三种方法： [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))、 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)和 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)。 [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) 允许接口用户要求对象指向其接口的另一个接口。 [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) 和 [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) 在接口上实现引用计数。

## <a name="see-also"></a>请参阅

[COM 简介](../atl/introduction-to-com.md)<br/>
[IUnknown 和接口继承](/windows/win32/com/iunknown-and-interface-inheritance)
