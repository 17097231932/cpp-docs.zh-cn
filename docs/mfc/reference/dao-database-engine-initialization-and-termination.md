---
description: 了解详细信息： DAO 数据库引擎初始化和终止
title: DAO 数据库引擎初始化和终止
ms.date: 09/17/2019
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 9e9b522d744eabc84074b201051151b80ed75d7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220391"
---
# <a name="dao-database-engine-initialization-and-termination"></a>DAO 数据库引擎初始化和终止

DAO 与 Access 数据库结合使用，并受 Office 2013 的支持。 DAO 3.6 是最终版本，被视为已过时。 使用 MFC DAO 对象时，必须先初始化 DAO 数据库引擎然后终止，您的应用程序或 DLL 才能退出。 `AfxDaoInit` 和 `AfxDaoTerm` 这两个函数将执行这些任务。

### <a name="dao-database-engine-initialization-and-termination"></a>DAO 数据库引擎初始化和终止

|名称|描述|
|-|-|
|[AfxDaoInit](#afxdaoinit)|初始化 DAO 数据库引擎。|
|[AfxDaoTerm](#afxdaoterm)|终止 DAO 数据库引擎。|

## <a name="afxdaoinit"></a><a name="afxdaoinit"></a> AfxDaoInit

此函数初始化 DAO 数据库引擎。

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>备注

大多数情况下，不需要调用， `AfxDaoInit` 因为应用程序会在需要时自动调用它。

有关相关信息以及调用的示例 `AfxDaoInit` ，请参阅 [技术说明 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

### <a name="requirements"></a>要求

  **标头** afxdao

## <a name="afxdaoterm"></a><a name="afxdaoterm"></a> AfxDaoTerm

此函数终止 DAO 数据库引擎。

```

void AfxDaoTerm();
```

### <a name="remarks"></a>备注

通常，只需在常规 MFC DLL 中调用此函数;当需要时，应用程序将自动调用 `AfxDaoTerm` 。

在常规 MFC Dll 中，在 `AfxDaoTerm` 函数之前调用 `ExitInstance` ，但在销毁所有 MFC DAO 对象之后。

有关相关信息，请参阅 [技术说明 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

### <a name="requirements"></a>要求

  **标头** afxdao

## <a name="see-also"></a>请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
