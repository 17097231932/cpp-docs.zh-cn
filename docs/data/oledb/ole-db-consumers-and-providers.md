---
description: 了解详细信息： OLE DB 使用者和提供者
title: OLE DB 使用者和提供程序
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB providers, OLE DB data architecture
- OLE DB providers
- OLE DB consumers, OLE DB data architecture
- OLE DB consumers
- OLE DB, data model
ms.assetid: 886cb39d-652b-4557-93f0-4b1b0754d8bc
ms.openlocfilehash: dedcbe7837cf7fad5bc9db8832e34edd3859a02b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317137"
---
# <a name="ole-db-consumers-and-providers"></a>OLE DB 使用者和提供程序

OLE DB 的体系结构使用使用者和提供者模型。 使用者发出数据请求。 提供程序通过将数据置于表格格式并将数据返回给使用者来响应这些请求。 使用者可以做出的任何调用都必须在提供程序中实现。

从技术上讲，使用者是指任何系统或应用程序代码 (不一定是通过 OLE DB 接口访问数据) OLE DB 组件。 接口是在提供程序中实现的。 因此，提供程序是任何实现 OLE DB 接口的软件组件，用于封装对数据的访问，并将其公开给其他对象 (也就是说，使用者) 。

对于角色，使用者调用 OLE DB 接口上的方法;OLE DB 提供程序实现所需的 OLE DB 接口。

OLE DB 避免了术语 "客户端" 和 "服务器"，因为这些角色并非始终有用，尤其是在 n 层情况下。 由于使用者可以是服务于其他组件的层上的组件，因此，若要调用客户端组件，则会造成混淆。 此外，提供程序有时更像是服务器的数据库驱动程序。

## <a name="see-also"></a>请参阅

[OLE DB 编程](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 编程概述](../../data/oledb/ole-db-programming-overview.md)
