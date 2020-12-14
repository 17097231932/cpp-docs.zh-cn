---
description: 了解详细信息： ExitInstance 成员函数
title: ExitInstance 成员函数
ms.date: 11/04/2016
f1_keywords: []
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
ms.openlocfilehash: a469d29c6b8dc2b822928293ee3bd083ccce95e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314719"
---
# <a name="exitinstance-member-function"></a>ExitInstance 成员函数

每次当应用程序的副本终止时，通常会调用[CWinApp](reference/cwinapp-class.md)类的[ExitInstance](reference/cwinapp-class.md#exitinstance)成员函数，这通常是用户退出应用程序的结果。

如果需要特殊清理处理（如释放图形设备接口 (GDI) 资源或释放在程序执行期间使用的内存），则重写 `ExitInstance`。 但是，标准项（如文档和视图）的清理由框架使用用于执行特定于这些对象的特殊清理的其他可重写函数提供。

## <a name="see-also"></a>请参阅

[CWinApp：应用程序类](cwinapp-the-application-class.md)
