---
description: 了解详细信息： CAcl 类
title: CAcl 类
ms.date: 11/04/2016
f1_keywords:
- CAcl
- ATLSECURITY/ATL::CAcl
- ATLSECURITY/ATL::CAcl::CAccessMaskArray
- ATLSECURITY/ATL::CAcl::CAceFlagArray
- ATLSECURITY/ATL::CAcl::CAceTypeArray
- ATLSECURITY/ATL::CAcl::CAcl
- ATLSECURITY/ATL::CAcl::GetAceCount
- ATLSECURITY/ATL::CAcl::GetAclEntries
- ATLSECURITY/ATL::CAcl::GetAclEntry
- ATLSECURITY/ATL::CAcl::GetLength
- ATLSECURITY/ATL::CAcl::GetPACL
- ATLSECURITY/ATL::CAcl::IsEmpty
- ATLSECURITY/ATL::CAcl::IsNull
- ATLSECURITY/ATL::CAcl::RemoveAce
- ATLSECURITY/ATL::CAcl::RemoveAces
- ATLSECURITY/ATL::CAcl::SetEmpty
- ATLSECURITY/ATL::CAcl::SetNull
helpviewer_keywords:
- CAcl class
ms.assetid: 20bcb9af-dc1c-4737-b923-3864776680d6
ms.openlocfilehash: 60c498336f1bfb5358dd8e5b2eb771456a84ce17
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165064"
---
# <a name="cacl-class"></a>CAcl 类

此类是 `ACL` (访问控制列表) 结构的包装器。

> [!IMPORTANT]
> 此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```cpp
class CAcl
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|[CAcl::CAccessMaskArray](#caccessmaskarray)|ACCESS_MASKs 的数组。|
|[CAcl::CAceFlagArray](#caceflagarray)|字节数组。|
|[CAcl::CAceTypeArray](#cacetypearray)|字节数组。|

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[CAcl::CAcl](#cacl)|构造函数。|
|[CAcl：： ~ CAcl](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CAcl::GetAceCount](#getacecount)|返回 (ACE) 对象的访问控制项的数目。|
|[CAcl::GetAclEntries](#getaclentries)|从对象中检索 (ACL) 项的访问控制列表 `CAcl` 。|
|[CAcl::GetAclEntry](#getaclentry)|检索对象中某个条目的所有相关信息 `CAcl` 。|
|[CAcl：： GetLength](#getlength)|返回 ACL 的长度。|
|[CAcl::GetPACL](#getpacl)|返回指向 ACL) 的程序包 (指针。|
|[CAcl：： IsEmpty](#isempty)|测试 `CAcl` 对象的项。|
|[CAcl：： IsNull](#isnull)|返回对象的状态 `CAcl` 。|
|[CAcl::RemoveAce](#removeace)|从对象中移除特定 ACE (访问控制项) `CAcl` 。|
|[CAcl::RemoveAces](#removeaces)|从应用于给定的中移除所有)  (访问控制项 `CAcl` `CSid` 。|
|[CAcl::SetEmpty](#setempty)|将 `CAcl` 对象标记为空。|
|[CAcl：： SetNull](#setnull)|将 `CAcl` 对象标记为 NULL。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CAcl：： operator const ACL *](#operator_const_acl__star)|将对象强制转换 `CAcl` 为 `ACL` 结构。|
|[CAcl：： operator =](#operator_eq)|赋值运算符。|

## <a name="remarks"></a>备注

`ACL`结构是 ACL (访问控制列表) 的标头。 ACL 包括)  (访问控制项的零个或多个 [ace](/windows/win32/SecAuthZ/access-control-entries) 的顺序列表。 ACL 中的各个 Ace 的编号为0到 *n-1*，其中 *n* 是 acl 中的 ace 的数量。 编辑 ACL 时，应用程序通过索引 (ACE 内的 ACE) 来引用访问控制项。

有两种 ACL 类型：

- 自主

- 系统

随机 ACL 由对象的所有者控制，或者由授予 WRITE_DAC 对对象的访问权限的任何人控制。 它指定特定用户和组对对象的访问权限。 例如，文件的所有者可以使用任意 ACL 来控制哪些用户和组可以和不能访问该文件。

对象也可以具有与之关联的系统级安全信息，以系统管理员控制的系统 ACL 的形式提供。 系统 ACL 可以允许系统管理员审核获取对象访问权限的任何尝试。

有关更多详细信息，请参阅 Windows SDK 中的 [ACL](/windows/win32/SecAuthZ/access-control-lists) 讨论。

有关 Windows 中的访问控制模型的简介，请参阅 Windows SDK 中的 [访问控制](/windows/win32/SecAuthZ/access-control) 。

## <a name="requirements"></a>要求

**标头：** atlsecurity。h

## <a name="caclcaccessmaskarray"></a><a name="caccessmaskarray"></a> CAcl::CAccessMaskArray

ACCESS_MASK 对象的数组。

```cpp
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```

### <a name="remarks"></a>备注

此 typedef 指定可用于存储 (Ace) 的访问控制项中使用的访问权限的数组类型。

## <a name="caclcaceflagarray"></a><a name="caceflagarray"></a> CAcl::CAceFlagArray

字节数组。

```cpp
typedef CAtlArray<BYTE> CAceFlagArray;
```

### <a name="remarks"></a>备注

此 typedef 指定用于定义 (ACE) 类型特定控件标志的访问控制项的数组类型。 有关可能的标志的完整列表，请参阅 [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) 定义。

## <a name="caclcacetypearray"></a><a name="cacetypearray"></a> CAcl::CAceTypeArray

字节数组。

```cpp
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>备注

此 typedef 指定用于定义 (ACE) 对象（如 ACCESS_ALLOWED_ACE_TYPE 或 ACCESS_DENIED_ACE_TYPE）的访问控制项的性质的数组类型。 有关可能的类型的完整列表，请参阅 [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) 定义。

## <a name="caclcacl"></a><a name="cacl"></a> CAcl::CAcl

构造函数。

```cpp
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>parameters

*rhs*<br/>
一个现有的 `CAcl` 对象。

### <a name="remarks"></a>备注

`CAcl`可以选择使用现有对象来创建对象 `CAcl` 。

## <a name="caclcacl"></a><a name="dtor"></a> CAcl：： ~ CAcl

析构函数。

```cpp
virtual ~CAcl() throw();
```

### <a name="remarks"></a>备注

析构函数释放由该对象获取的任何资源。

## <a name="caclgetacecount"></a><a name="getacecount"></a> CAcl::GetAceCount

返回 (ACE) 对象的访问控制项的数目。

```cpp
virtual UINT GetAceCount() const throw() = 0;
```

### <a name="return-value"></a>返回值

返回对象中的 ACE 项的数目 `CAcl` 。

## <a name="caclgetaclentries"></a><a name="getaclentries"></a> CAcl::GetAclEntries

从对象中检索 (ACL) 项的访问控制列表 `CAcl` 。

```cpp
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```

### <a name="parameters"></a>parameters

*pSids*<br/>
指向 [CSid](../../atl/reference/csid-class.md) 对象的数组的指针。

*pAccessMasks*<br/>
访问掩码。

*pAceTypes*<br/>
 (ACE) 类型的访问控制项。

*pAceFlags*<br/>
ACE 标志。

### <a name="remarks"></a>备注

此方法用对象中包含的每个 ACE 对象的详细信息填充数组参数 `CAcl` 。 如果不需要特定数组的详细信息，请使用 NULL。

每个数组的内容彼此对应，也就是说，数组的第一个元素 `CAccessMaskArray` 对应于数组中的第一个元素 `CSidArray` ，依此类推。

有关 ACE 类型和标志的详细信息，请参阅 [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) 。

## <a name="caclgetaclentry"></a><a name="getaclentry"></a> CAcl::GetAclEntry

检索有关访问控制列表中某个条目 (ACL) 的所有信息。

```cpp
void GetAclEntry(
    UINT nIndex,
    CSid* pSid,
    ACCESS_MASK* pMask = NULL,
    BYTE* pType = NULL,
    BYTE* pFlags = NULL,
    GUID* pObjectType = NULL,
    GUID* pInheritedObjectType = NULL) const throw(...);
```

### <a name="parameters"></a>parameters

*nIndex*<br/>
要检索的 ACL 项的索引。

*pSid*<br/>
ACL 条目应用到的 [CSid](../../atl/reference/csid-class.md) 对象。

*pMask*<br/>
指定授予或拒绝访问权限的掩码。

*pType*<br/>
ACE 类型。

*pFlags*<br/>
ACE 标志。

*pObjectType*<br/>
对象类型。 如果未在 ACE 中指定该对象类型，则将设置为 GUID_NULL; 如果 ACE 不是 OBJECT ACE，则设置为。

*pInheritedObjectType*<br/>
继承的对象类型。 如果未在 ACE 中指定继承的对象类型，或者如果 ACE 不是 OBJECT ACE，则将设置为 GUID_NULL。

### <a name="remarks"></a>备注

此方法将检索有关单个 ACE 的所有信息，并提供比 [CAcl：： GetAclEntries](#getaclentries) 单独提供的信息更多的信息。

有关 ACE 类型和标志的详细信息，请参阅 [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) 。

## <a name="caclgetlength"></a><a name="getlength"></a> CAcl：： GetLength

返回 (ACL) 的访问控制列表的长度。

```cpp
UINT GetLength() const throw();
```

### <a name="return-value"></a>返回值

返回保存结构所需的所需长度（以字节为单位） `ACL` 。

## <a name="caclgetpacl"></a><a name="getpacl"></a> CAcl::GetPACL

返回指向访问控制列表 (ACL) 的指针。

```cpp
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>返回值

返回指向结构的指针 `ACL` 。

## <a name="caclisempty"></a><a name="isempty"></a> CAcl：： IsEmpty

测试 `CAcl` 对象的项。

```cpp
bool IsEmpty() const throw();
```

### <a name="remarks"></a>备注

如果 `CAcl` 对象不为 NULL，则返回 TRUE，并且不包含任何项。 如果 `CAcl` 对象为 NULL 或包含至少一个条目，则返回 FALSE。

## <a name="caclisnull"></a><a name="isnull"></a> CAcl：： IsNull

返回对象的状态 `CAcl` 。

```cpp
bool IsNull() const throw();
```

### <a name="return-value"></a>返回值

如果 `CAcl` 对象为 NULL，则返回 TRUE，否则返回 FALSE。

## <a name="cacloperator-const-acl-"></a><a name="operator_const_acl__star"></a> CAcl：： operator const ACL *

将对象强制转换 `CAcl` 为 `ACL` (的访问控制列表) 结构。

```cpp
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>备注

返回结构的地址 `ACL` 。

## <a name="cacloperator-"></a><a name="operator_eq"></a> CAcl：： operator =

赋值运算符。

```cpp
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>parameters

*rhs*<br/>
`CAcl`要分配给现有对象的。

### <a name="return-value"></a>返回值

返回对已更新的对象的引用 `CAcl` 。

## <a name="caclremoveace"></a><a name="removeace"></a> CAcl::RemoveAce

从对象中移除特定 ACE (访问控制项) `CAcl` 。

```cpp
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>parameters

*nIndex*<br/>
要移除的 ACE 项的索引。

### <a name="remarks"></a>备注

此方法从 [CAtlArray：： RemoveAt](../../atl/reference/catlarray-class.md#removeat)派生。

## <a name="caclremoveaces"></a><a name="removeaces"></a> CAcl::RemoveAces

从应用于给定的的中移除)  (访问控制项 `CAcl` `CSid` 。

```cpp
bool RemoveAces(const CSid& rSid) throw(...)
```

### <a name="parameters"></a>parameters

*rSid*<br/>
对 `CSid` 对象的引用。

## <a name="caclsetempty"></a><a name="setempty"></a> CAcl::SetEmpty

将 `CAcl` 对象标记为空。

```cpp
void SetEmpty() throw();
```

### <a name="remarks"></a>备注

`CAcl`可以设置为空或 NULL：这两个状态是不同的。

## <a name="caclsetnull"></a><a name="setnull"></a> CAcl：： SetNull

将 `CAcl` 对象标记为 NULL。

```cpp
void SetNull() throw();
```

### <a name="remarks"></a>备注

`CAcl`可以设置为空或 NULL：这两个状态是不同的。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[安全全局函数](../../atl/reference/security-global-functions.md)
