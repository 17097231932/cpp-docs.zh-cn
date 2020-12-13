---
description: 了解详细信息：活动文档
title: 活动文档
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC]
- active documents [MFC], requirements
- view objects [MFC], requirements
- OLE [MFC], active documents
- views [MFC], active documents
- active documents [MFC], views
ms.assetid: 1378f18e-aaa6-420b-8501-4b974905baa0
ms.openlocfilehash: cae0eda775670867d5e36b4f2b9ec895a5dc3eb7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150301"
---
# <a name="active-documents"></a>活动文档

活动文档扩展了 OLE 的复合文档技术。 这些扩展是以管理视图的其他界面的形式提供的，因此对象可在容器中正常运行，并且保持对其显示和打印功能的控制。 此过程使在外部框架（如 Microsoft Office Binder 或 Microsoft Internet Explorer）和本机框架（如产品自己的视区）中显示文档成为可能。

本部分介绍 [活动文档](#requirements_for_active_documents)的功能要求。 活动文档拥有一组数据并对其中可保存和检索数据的存储具有访问权限。 它可以针对其数据创建和管理一个或多个视图。 除了支持 OLE 文档的通用嵌入和就地激活接口之外，活动文档还传递其功能以通过 `IOleDocument` 创建视图。 通过此接口，容器可要求创建（并且可能枚举）活动文档可显示的视图。 通过此接口，活动文档还可提供有关自身的杂项信息，如它是否支持多个视图或复杂矩形。

下面是 `IOleDocument` 接口。 请注意， `IEnumOleDocumentViews` 接口是类型的标准 OLE 枚举器 `IOleDocumentView*` 。

```
interface IOleDocument : IUnknown
    {
    HRESULT CreateView(
        [in] IOleInPlaceSite *pIPSite,
        [in] IStream *pstm,
        [in] DWORD dwReserved,
        [out] IOleDocumentView **ppView);

    HRESULT GetDocMiscStatus([out] DWORD *pdwStatus);

    HRESULT EnumViews(
        [out] IEnumOleDocumentViews **ppEnum,
        [out] IOleDocumentView **ppView);
    }
```

每个活动文档必须具有一个视图框架提供程序以及此接口。 如果文档未嵌入容器中，则活动文档服务器自身必须提供视图框架。 但是，在活动文档容器中嵌入活动文档后，容器将提供视图框架。

活动文档可以为其数据创建一种或多种类型的 [视图](#requirements_for_view_objects) (例如，普通、大纲、页面布局等) 。 视图的行为像通过其可查看数据的筛选器。 即使文档只有一种类型的视图，您可能仍希望支持多个视图，作为支持新窗口功能的一种方法 (例如，Office 应用程序中 "**窗口**" 菜单上的 "**新建窗口**" 项) 。

## <a name="requirements-for-active-documents"></a><a name="requirements_for_active_documents"></a> 活动文档的要求

可在活动文档容器中显示的活动文档必须：

- 通过实现 `IPersistStorage`，使用 OLE 的复合文件作为存储机制。

- 支持 OLE 文档的基本嵌入功能，包括 **Create From File**。 这需要 `IPersistFile`、`IOleObject` 和 `IDataObject` 接口。

- 支持一个或多个视图，每个视图均能就地激活。 也就是说，视图必须支持接口以及 `IOleDocumentView` 接口 `IOleInPlaceObject` ，并 `IOleInPlaceActiveObject` 使用容器的 `IOleInPlaceSite` 和 `IOleInPlaceFrame` 接口)  (。

- 支持标准活动文档接口 `IOleDocument`、`IOleCommandTarget` 和 `IPrint`。

这些需求中暗示了解何时以及如何使用容器端接口。

## <a name="requirements-for-view-objects"></a><a name="requirements_for_view_objects"></a> 视图对象的要求

活动文档可以为其数据创建一个或多个视图。 从功能上来说，这些视图类似于特定方法上的用于显示数据的端口。 如果活动文档只支持单个视图，则可使用单个类实现活动文档及其支持的单个视图。 `IOleDocument::CreateView` 返回相同对象的 `IOleDocumentView` 接口指针。

若要在活动文档容器中表示，视图组件除了支持外，还必须支持 `IOleInPlaceObject` `IOleInPlaceActiveObject` `IOleDocumentView` ：

```
interface IOleDocumentView : IUnknown
    {
    HRESULT SetInPlaceSite([in] IOleInPlaceSite *pIPSite);
    HRESULT GetInPlaceSite([out] IOleInPlaceSite **ppIPSite);
    HRESULT GetDocument([out] IUnknown **ppunk);
    [input_sync] HRESULT SetRect([in] LPRECT prcView);
    HRESULT GetRect([in] LPRECT prcView);
    [input_sync] HRESULT SetRectComplex(
        [in] LPRECT prcView,
        [in] LPRECT prcHScroll,
        [in] LPRECT prcVScroll,
        [in] LPRECT prcSizeBox);
    HRESULT Show([in] BOOL fShow);
    HRESULT UIActivate([in] BOOL fUIActivate);
    HRESULT Open(void);
    HRESULT CloseView([in] DWORD dwReserved);
    HRESULT SaveViewState([in] IStream *pstm);
    HRESULT ApplyViewState([in] IStream *pstm);
    HRESULT Clone(
        [in] IOleInPlaceSite *pIPSiteNew,
        [out] IOleDocumentView **ppViewNew);
    }
```

每个视图都具有关联视图站点，其将封装视图框架和视区（窗口中的 HWND 和矩形区域）。 站点通过标准接口公开此功能 `IOleInPlaceSite` 。 请注意，一个 HWND 上可具有多个视区。

通常，视图的每种类型具有不同的打印表示形式。 因此，视图和对应的视图站点应分别实现打印接口 `IPrint` 和 `IContinueCallback`。 打印开始时，视图框架必须与视图提供程序进行协商 `IPrint` ，以便正确打印页眉、页脚、边距和相关元素。 视图提供程序通过 `IContinueCallback` 向框架通知打印相关事件。 有关使用这些接口的详细信息，请参阅 [编程打印](programmatic-printing.md)。

请注意，如果活动文档仅支持单个视图，则可使用单个具体类实现活动文档和其支持的单个视图。 `IOleDocument::CreateView` 只返回相同对象的 `IOleDocumentView` 接口指针。 总之，当只需要一个视图时不必具有两个不同的对象实例。

视图对象也可以是命令目标。 通过实现 `IOleCommandTarget` 视图可接收源自容器的用户界面的命令 (例如 "**文件**" 菜单上的 "**新建**"、"**打开**"、"**另存为**"、"**打印**"、"**编辑**" 菜单上的 "**复制**"、"**粘贴**"、"**撤消**") 。 有关详细信息，请参阅 [消息处理和命令目标](message-handling-and-command-targets.md)。

## <a name="see-also"></a>请参阅

[活动文档包容](active-document-containment.md)
