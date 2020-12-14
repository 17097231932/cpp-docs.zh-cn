---
description: '了解详细信息：框架 (MFC) '
title: 框架 (MFC)
ms.date: 09/17/2019
helpviewer_keywords:
- encapsulation [MFC], Win32 API
- MFC, application framework
- wrapper classes [MFC], explained
- Win32 [MFC], API encapsulation by MFC
- application framework [MFC], about MFC application framework
- APIs [MFC], encapsulation by MFC Win32
- encapsulation [MFC]
- Windows API [MFC], encapsulation by MFC
- encapsulated Win32 API [MFC]
ms.assetid: 3be0fec8-9843-4119-ae42-ece993ef500b
ms.openlocfilehash: 12e5a28e231dfadec867213ebf1cea6fd6ae7300
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193482"
---
# <a name="framework-mfc"></a>框架 (MFC)

在使用 Microsoft 基础类 (MFC) 库框架时很大程度上基于几个主要的类和 Visual C++ 工具。 一些类封装了 Win32 应用程序编程接口 (API) 的一大部分。 其他类封装了应用程序概念，如文档、视图和应用程序本身。 还有其他类封装了 OLE 功能以及 ODBC 和 DAO 数据访问功能。   (DAO 受 Office 2013 的支持。 DAO 3.6 是最终版本，被视为已过时。 ) 

例如，Win32 的窗口概念由 MFC 类 `CWnd` 封装。 也就是说，名为 `CWnd` 的 C++ 类封装或“包装”了表示 Windows 窗口的 `HWND` 句柄。 同样，`CDialog` 类封装了 Win32 对话框。

以 C++ 类 `CWnd` 为例，封装意味着它包含了 `HWND` 类型的成员变量，并且它的成员函数封装了对采用 `HWND` 作为参数的 Win32 函数的调用。 类成员函数通常具有与其所封装的 Win32 函数相同的名称。

## <a name="in-this-section"></a>本节内容

[SDI 和 MDI](sdi-and-mdi.md)

[文档、视图和框架](documents-views-and-the-framework.md)

[向导和资源编辑器](wizards-and-the-resource-editors.md)

## <a name="in-related-sections"></a>相关章节

[基于框架生成](building-on-the-framework.md)

[框架如何调用你的代码](how-the-framework-calls-your-code.md)

[CWinApp：应用程序类](cwinapp-the-application-class.md)

[文档模板和文档/视图创建过程](document-templates-and-the-document-view-creation-process.md)

[消息处理和映射](message-handling-and-mapping.md)

[窗口对象](window-objects.md)

## <a name="see-also"></a>请参阅

[使用类编写适用于 Windows 的应用程序](using-the-classes-to-write-applications-for-windows.md)
