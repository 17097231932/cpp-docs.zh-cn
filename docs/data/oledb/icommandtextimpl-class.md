---
description: 了解详细信息： ICommandTextImpl 类
title: ICommandTextImpl 类
ms.date: 11/04/2016
f1_keywords:
- ICommandText
- GetCommandText
- ICommandTextImpl.GetCommandText
- ICommandTextImpl::GetCommandText
- ATL::ICommandTextImpl::m_strCommandText
- ICommandTextImpl<T>::m_strCommandText
- m_strCommandText
- ICommandTextImpl.m_strCommandText
- ICommandTextImpl::m_strCommandText
- ATL::ICommandTextImpl<T>::m_strCommandText
- ATL.ICommandTextImpl.m_strCommandText
- ICommandTextImpl.SetCommandText
- ICommandTextImpl::SetCommandText
- SetCommandText
helpviewer_keywords:
- ICommandText class
- GetCommandText method
- m_strCommandText
- SetCommandText method
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
ms.openlocfilehash: 4b48b9f8f2ee535a648681064cc6b1083c76e489
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287367"
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl 类

提供 [ICommandText](/previous-versions/windows/desktop/ms714914(v=vs.85)) 接口的实现。

## <a name="syntax"></a>语法

```cpp
template <class T >
class ATL_NO_VTABLE ICommandTextImpl
   : public ICommandImpl<T, ICommandText>
```

### <a name="parameters"></a>parameters

*T*<br/>
派生自的 command 类 `ICommandTextImpl` 。

## <a name="requirements"></a>要求

**标头：** altdb

## <a name="members"></a>成员

### <a name="interface-methods"></a>接口方法

| 名称 | 描述 |
|-|-|
|[GetCommandText](#getcommandtext)|返回由对 [SetCommandText](#setcommandtext)的最后一次调用设置的文本命令。|
|[SetCommandText](#setcommandtext)|设置命令文本，并替换现有的命令文本。|

### <a name="data-members"></a>数据成员

| 名称 | 描述 |
|-|-|
|[m_strCommandText](#strcommandtext)|存储命令文本。|

## <a name="remarks"></a>备注

命令的必需接口。

## <a name="icommandtextimplgetcommandtext"></a><a name="getcommandtext"></a> ICommandTextImpl：： GetCommandText

返回由对 [SetCommandText](#setcommandtext)的最后一次调用设置的文本命令。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(GetCommandText)(GUID * pguidDialect,
   LPOLESTR * ppwszCommand);
```

#### <a name="parameters"></a>parameters

请参阅 *OLE DB 程序员参考* 中的 [ICommandText：： GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) 。 默认情况下，将忽略 *pguidDialect* 参数。

## <a name="icommandtextimplsetcommandtext"></a><a name="setcommandtext"></a> ICommandTextImpl：： SetCommandText

设置命令文本，并替换现有的命令文本。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(SetCommandText)(REFGUID rguidDialect,
   LPCOLESTR pwszCommand);
```

#### <a name="parameters"></a>parameters

请参阅 *OLE DB 程序员参考* 中的 [ICommandText：： SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) 。

## <a name="icommandtextimplm_strcommandtext"></a><a name="strcommandtext"></a> ICommandTextImpl：： m_strCommandText

存储命令文本字符串。

### <a name="syntax"></a>语法

```cpp
CComBSTR m_strCommandText;
```

## <a name="see-also"></a>请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
