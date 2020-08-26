---
title: IColumnsInfoImpl 类
ms.date: 11/04/2016
f1_keywords:
- ATL.IColumnsInfoImpl<T>
- ATL::IColumnsInfoImpl
- IColumnsInfoImpl
- ATL.IColumnsInfoImpl
- ATL::IColumnsInfoImpl<T>
- ATL::IColumnsInfoImpl::GetColumnInfo
- ATL.IColumnsInfoImpl.GetColumnInfo
- ATL::IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl::GetColumnInfo
- IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl.GetColumnInfo
- IColumnsInfoImpl<T>::MapColumnIDs
- MapColumnIDs
- ATL::IColumnsInfoImpl::MapColumnIDs
- IColumnsInfoImpl.MapColumnIDs
- ATL::IColumnsInfoImpl<T>::MapColumnIDs
- IColumnsInfoImpl::MapColumnIDs
- ATL.IColumnsInfoImpl<T>.MapColumnIDs
- ATL.IColumnsInfoImpl.MapColumnIDs
helpviewer_keywords:
- IColumnsInfoImpl class
- GetColumnInfo method
- MapColumnIDs method
ms.assetid: ba74c1c5-2eda-4452-8b57-84919fa0d066
ms.openlocfilehash: 05e902e09c51012bd456751fb701ce2508a2fc16
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845596"
---
# <a name="icolumnsinfoimpl-class"></a>IColumnsInfoImpl 类

提供 [IColumnsInfo](/previous-versions/windows/desktop/ms724541(v=vs.85)) 接口的实现。

## <a name="syntax"></a>语法

```cpp
template <class T>
class ATL_NO_VTABLE IColumnsInfoImpl :
   public IColumnsInfo,
   public CDBIDOps
```

### <a name="parameters"></a>参数

*T*<br/>
派生自的类 `IColumnsInfoImpl` 。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

| 名称 | 说明 |
|-|-|
|[GetColumnInfo](#getcolumninfo)|返回大多数使用方需要的列元数据。|
|[MapColumnIDs](#mapcolumnids)|返回行集合中列序号的数组，这些列序号由指定的列 ID 标识。|

## <a name="remarks"></a>注解

行集和命令的必需接口。 若要修改提供程序的实现行为 `IColumnsInfo` ，需要修改提供程序列映射。

## <a name="icolumnsinfoimplgetcolumninfo"></a><a name="getcolumninfo"></a> IColumnsInfoImpl：： GetColumnInfo

返回大多数使用方需要的列元数据。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (GetColumnInfo)(DBORDINAL* pcColumns,
   DBCOLUMNINFO** prgInfo,
   OLECHAR** ppStringsBuffer);
```

#### <a name="parameters"></a>参数

请参阅*OLE DB 程序员参考*中的[IColumnsInfo：： GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) 。

## <a name="icolumnsinfoimplmapcolumnids"></a><a name="mapcolumnids"></a> IColumnsInfoImpl：： MapColumnIDs

返回行集合中列序号的数组，这些列序号由指定的列 ID 标识。

### <a name="syntax"></a>语法

```cpp
STDMETHOD (MapColumnIDs)(DBORDINAL cColumnIDs,
   const DBID rgColumnIDs[],
   DBORDINAL rgColumns[]);
```

#### <a name="parameters"></a>参数

请参阅*OLE DB 程序员参考*中的[IColumnsInfo：： MapColumnIDs](/previous-versions/windows/desktop/ms714200(v=vs.85)) 。

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
