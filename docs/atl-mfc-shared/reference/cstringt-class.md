---
title: '**`CStringT`** 班级'
description: Microsoft ATL 类的 API 参考 **`CStringT`**
ms.date: 12/06/2020
f1_keywords:
- CStringT
- CSTRINGT/ATL::CStringT
- CSTRINGT/ATL::CStringT::CStringT
- CSTRINGT/ATL::CStringT::AllocSysString
- CSTRINGT/ATL::CStringT::AnsiToOem
- CSTRINGT/ATL::CStringT::AppendFormat
- CSTRINGT/ATL::CStringT::Collate
- CSTRINGT/ATL::CStringT::CollateNoCase
- CSTRINGT/ATL::CStringT::Compare
- CSTRINGT/ATL::CStringT::CompareNoCase
- CSTRINGT/ATL::CStringT::Delete
- CSTRINGT/ATL::CStringT::Find
- CSTRINGT/ATL::CStringT::FindOneOf
- CSTRINGT/ATL::CStringT::Format
- CSTRINGT/ATL::CStringT::FormatMessage
- CSTRINGT/ATL::CStringT::FormatMessageV
- CSTRINGT/ATL::CStringT::FormatV
- CSTRINGT/ATL::CStringT::GetEnvironmentVariable
- CSTRINGT/ATL::CStringT::Insert
- CSTRINGT/ATL::CStringT::Left
- CSTRINGT/ATL::CStringT::LoadString
- CSTRINGT/ATL::CStringT::MakeLower
- CSTRINGT/ATL::CStringT::MakeReverse
- CSTRINGT/ATL::CStringT::MakeUpper
- CSTRINGT/ATL::CStringT::Mid
- CSTRINGT/ATL::CStringT::OemToAnsi
- CSTRINGT/ATL::CStringT::Remove
- CSTRINGT/ATL::CStringT::Replace
- CSTRINGT/ATL::CStringT::ReverseFind
- CSTRINGT/ATL::CStringT::Right
- CSTRINGT/ATL::CStringT::SetSysString
- CSTRINGT/ATL::CStringT::SpanExcluding
- CSTRINGT/ATL::CStringT::SpanIncluding
- CSTRINGT/ATL::CStringT::Tokenize
- CSTRINGT/ATL::CStringT::Trim
- CSTRINGT/ATL::CStringT::TrimLeft
- CSTRINGT/ATL::CStringT::TrimRight
helpviewer_keywords:
- strings [C++], in ATL
- shared classes, CStringT
- CStringT class
ms.openlocfilehash: f9ec5c02aa1ed9377a38d30d9a4152af5e164d58
ms.sourcegitcommit: 7b131db4ed39bddb4a456ebea402f47c5cbd69d3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/07/2020
ms.locfileid: "96776539"
---
# <a name="cstringt-class"></a>`CStringT` 类

此类表示一个 **`CStringT`** 对象。

## <a name="syntax"></a>语法

```cpp
template<typename BaseType, class StringTraits>
class CStringT :
    public CSimpleStringT<BaseType,
        _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>::c_bIsMFCDLLTraits>
```

#### <a name="parameters"></a>参数

*`BaseType`*\
字符串类的字符类型。 可以是以下值之一：

- **`char`** 为 ANSI 字符串)  (。

- **`wchar_t`**)  (Unicode 字符串。

- **`TCHAR`** 为 ANSI 和 Unicode 字符串)  (。

*`StringTraits`*\
确定字符串类是否需要 C Run-Time (CRT) 库支持和字符串资源所在位置。 可以是以下值之一：

- **`StrTraitATL<wchar_t | char | TCHAR, ChTraitsCRT<wchar_t | char | TCHAR>>`**

   类需要 CRT 支持，并在通过 `m_hInstResource` (应用程序 module 类的成员) 指定的模块中搜索资源字符串。

- **`StrTraitATL<wchar_t | char | TCHAR, ChTraitsOS<wchar_t | char |TCHAR>>`**

   类不要求 CRT 支持，并在指定的模块中搜索资源字符串 `m_hInstResource` (由应用程序的 module 类) 的成员进行。

- **`StrTraitMFC<wchar_t | char | TCHAR, ChTraitsCRT<wchar_t | char | TCHAR>>`**

   类需要 CRT 支持，并使用标准 MFC 搜索算法搜索资源字符串。

- **`StrTraitMFC<wchar_t | char | TCHAR, ChTraitsOS<wchar_t | char | TCHAR>>`**

   类不要求 CRT 支持，并使用标准 MFC 搜索算法搜索资源字符串。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|“属性”|描述|
|----------|-----------------|
|[`CStringT::CStringT`](#cstringt)|**`CStringT`** 以多种方式构造对象。|
|[`CStringT::~CStringT`](#_dtorcstringt)|销毁 **`CStringT`** 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[`CStringT::AllocSysString`](#allocsysstring)|`BSTR`从数据分配 **`CStringT`** 。|
|[`CStringT::AnsiToOem`](#ansitooem)|进行从 ANSI 字符集到 OEM 字符集的就地转换。|
|[`CStringT::AppendFormat`](#appendformat)|将格式化的数据追加到现有 **`CStringT`** 对象。|
|[`CStringT::Collate`](#collate)|将两个字符串 (区分大小写的字符串进行比较，使用特定于区域设置的信息) 。|
|[`CStringT::CollateNoCase`](#collatenocase)|比较不区分大小写 (两个字符串，) 使用特定于区域设置的信息。|
|[`CStringT::Compare`](#compare)|比较区分大小写)  (两个字符串。|
|[`CStringT::CompareNoCase`](#comparenocase)|比较不区分大小写的)  (两个字符串。|
|[`CStringT::Delete`](#delete)|删除字符串中的一个或多个字符。|
|[`CStringT::Find`](#find)|查找较大字符串内的字符或子字符串。|
|[`CStringT::FindOneOf`](#findoneof)|从集中查找第一个匹配的字符。|
|[`CStringT::Format`](#format)|将字符串的格式设置为 `sprintf` 。|
|[`CStringT::FormatMessage`](#formatmessage)|设置消息字符串的格式。|
|[`CStringT::FormatMessageV`](#formatmessagev)|使用变量参数列表设置消息字符串的格式。|
|[`CStringT::FormatV`](#formatv)|使用参数的变量列表设置字符串的格式。|
|[`CStringT::GetEnvironmentVariable`](#getenvironmentvariable)|将字符串设置为指定环境变量的值。|
|[`CStringT::Insert`](#insert)|在字符串中的给定索引处插入单个字符或子字符串。|
|[`CStringT::Left`](#left)|提取字符串的左侧部分。|
|[`CStringT::LoadString`](#loadstring)|**`CStringT`** 从 Windows 资源加载现有对象。|
|[`CStringT::MakeLower`](#makelower)|将此字符串中的所有字符转换为小写字符。|
|[`CStringT::MakeReverse`](#makereverse)|反转字符串。|
|[`CStringT::MakeUpper`](#makeupper)|将此字符串中的所有字符都转换为大写字符。|
|[`CStringT::Mid`](#mid)|提取字符串的中间部分。|
|[`CStringT::OemToAnsi`](#oemtoansi)|将从 OEM 字符集就地转换为 ANSI 字符集。|
|[`CStringT::Remove`](#remove)|从字符串中移除指定的字符。|
|[`CStringT::Replace`](#replace)|将所指示的字符替换为其他字符。|
|[`CStringT::ReverseFind`](#reversefind)|查找较大字符串中的字符;从末尾开始。|
|[`CStringT::Right`](#right)|提取字符串的右侧部分。|
|[`CStringT::SetSysString`](#setsysstring)|`BSTR`使用对象中的数据设置现有对象 **`CStringT`** 。|
|[`CStringT::SpanExcluding`](#spanexcluding)|提取字符串中的字符（从第一个字符开始，该字符不在标识的字符集中） `pszCharSet` 。|
|[`CStringT::SpanIncluding`](#spanincluding)|提取只包含集内的字符的子字符串。|
|[`CStringT::Tokenize`](#tokenize)|提取目标字符串中指定的令牌。|
|[`CStringT::Trim`](#trim)|剪裁字符串中的所有前导和尾随空格字符。|
|[`CStringT::TrimLeft`](#trimleft)|剪裁字符串中的前导空格字符。|
|[`CStringT::TrimRight`](#trimright)|从字符串中剪裁尾随空格字符。|

### <a name="operators"></a>运算符

|名称|描述|
|-|-|
|[`CStringT::operator =`](#operator_eq)|将新值分配给 **`CStringT`** 对象。|
|[`CStringT::operator +`](#operator_add)|连接两个字符串，或一个字符和一个字符串。|
|[`CStringT::operator +=`](#operator_add_eq)|将新字符串连接到现有字符串的末尾。|
|[`CStringT::operator ==`](#operator_eq_eq)|确定两个字符串是否逻辑上相等。|
|[`CStringT::operator !=`](#operator_neq)|确定两个字符串是否不以逻辑方式相等。|
|[`CStringT::operator <`](#operator_lt)|确定运算符左侧的字符串是否小于右侧的字符串的位置。|
|[`CStringT::operator >`](#operator_gt)|确定运算符左侧的字符串是否大于右侧的字符串的位置。|
|[`CStringT::operator <=`](#operator_lt_eq)|确定位于运算符左侧的字符串是否小于或等于右侧的字符串的。|
|[`CStringT::operator >=`](#operator_gt_eq)|确定位于运算符左侧的字符串是否大于或等于右侧的字符串的。|

## <a name="remarks"></a>备注

**`CStringT`** 继承自 [CSimpleStringT 类](../../atl-mfc-shared/reference/csimplestringt-class.md)。 高级功能（如字符操作、排序和搜索）是通过实现的 **`CStringT`** 。

> [!NOTE]
> **`CStringT`** 对象能够引发异常。 如果 **`CStringT`** 出于任何原因而导致对象内存不足，就会出现这种情况。

**`CStringT`** 对象由长度可变的字符序列组成。 **`CStringT`** 使用类似于基本的语法来提供函数和运算符。 串联和比较运算符以及简化的内存管理使 **`CStringT`** 对象比普通字符数组更易于使用。

> [!NOTE]
> 尽管可以创建 **`CStringT`** 包含嵌入的 null 字符的实例，但是我们建议您不要这样做。 对 **`CStringT`** 包含嵌入的 null 字符的对象调用方法和运算符可能会产生意外的结果。

通过使用和参数的不同 `BaseType` 组合 `StringTraits` ， **`CStringT`** 对象可以是以下类型，这些类型已经由 ATL 库预定义。

如果在 ATL 应用程序中使用：

`CString`、 `CStringA` 和 `CStringW` 将从 MFC dll 导出 ( # A0) ，从不从用户 dll 中导出。 这样做是为了防止多次 **`CStringT`** 定义。

> [!NOTE]
> 如果你的代码包含 [使用 CStringT 导出字符串类](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md)中所述的链接器错误的解决方法，则应删除该代码。 不再需要它。

基于 MFC 的应用程序中提供了以下字符串类型：

|CStringT 类型|声明|
|-------------------|-----------------|
|`CStringA`|具有 CRT 支持的 ANSI 字符类型字符串。|
|`CStringW`|支持 CRT 的 Unicode 字符类型字符串。|
|`CString`|ANSI 和 Unicode 字符类型都支持 CRT。|

以下字符串类型在定义的项目中提供 `ATL_CSTRING_NO_CRT` ：

|CStringT 类型|声明|
|-------------------|-----------------|
|`CAtlStringA`|不支持 CRT 的 ANSI 字符类型字符串。|
|`CAtlStringW`|不支持 CRT 的 Unicode 字符类型字符串。|
|`CAtlString`|不支持 CRT 的 ANSI 和 Unicode 字符类型。|

以下字符串类型在未定义的项目中可用 `ATL_CSTRING_NO_CRT` ：

|CStringT 类型|声明|
|-------------------|-----------------|
|`CAtlStringA`|具有 CRT 支持的 ANSI 字符类型字符串。|
|`CAtlStringW`|支持 CRT 的 Unicode 字符类型字符串。|
|`CAtlString`|ANSI 和 Unicode 字符类型都支持 CRT。|

`CString` 对象还具有以下特征：

- **`CStringT`** 由于串联操作的原因，对象可能会增长。

- **`CStringT`** 对象遵循 "值语义"。 将 **`CStringT`** 对象视为实际的字符串，而不是指向字符串的指针。

- 可以自由替换 **`CStringT`** `PCXSTR` 函数参数的对象。

- 字符串缓冲区的自定义内存管理。 有关详细信息，请参阅 [内存管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="cstringt-predefined-types"></a>CStringT 预定义类型

由于 **`CStringT`** 使用模板自变量定义字符类型 ([wchar_t](../../c-runtime-library/standard-types.md) 或 [char](../../c-runtime-library/standard-types.md)) 受支持，因此方法参数类型可能会很复杂。 若要简化此问题，请在整个类中定义和使用一组预定义类型 **`CStringT`** 。 下表列出了各种类型：

|名称|描述|
|----------|-----------------|
|`XCHAR`|单个字符 (**`wchar_t`** **`char`** 与对象具有相同字符类型的或) **`CStringT`** 。|
|`YCHAR`|单个字符 (**`wchar_t`** 或 **`char`**) 与对象相反的字符类型 **`CStringT`** 。|
|`PXSTR`|一个指向字符串的指针，该字符串 **`wchar_t`** **`char`**)  (与 * * * * * * `CStringT` * * * * * * * * * * * * * * * * * * * * * *|
|`PYSTR`|指向字符串的指针，该字符串 (**`wchar_t`** 或 **`char`** 与对象具有相反字符类型的) **`CStringT`** 。|
|`PCXSTR`|指向字符串的指针， **`const`** 该字符串 (**`wchar_t`** **`char`** 与对象具有相同字符类型的或) **`CStringT`** 。|
|`PCYSTR`|指向字符串的指针， **`const`** 该字符串 (**`wchar_t`** 或 **`char`** 与对象具有相反字符类型的) **`CStringT`** 。|

> [!NOTE]
> 以前使用过的 (的未记录方法的代码 `CString` （如 `AssignCopy`) ）必须替换为使用以下 (的记录方法的代码，如 **`CStringT`** `GetBuffer` 或 `ReleaseBuffer`) 。 这些方法是从继承的 `CSimpleStringT` 。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)

**`CStringT`**

## <a name="requirements"></a>要求

|标头|用于|
|------------|-------------|
|cstringt|仅限 MFC 的字符串对象|
|atlstr。h|非 MFC 字符串对象|

## <a name="cstringtallocsysstring"></a><a name="allocsysstring"></a> `CStringT::AllocSysString`

分配类型的自动化兼容字符串， `BSTR` 并将对象的内容复制到其中 **`CStringT`** ，包括终止 null 字符。

```cpp
BSTR AllocSysString() const;
```

### <a name="return-value"></a>返回值

新分配的字符串。

### <a name="remarks"></a>备注

在 MFC 程序中，如果存在内存不足的情况，则会引发 [CMemoryException 类](../../mfc/reference/cmemoryexception-class.md) 。 在 ATL 程序中，将引发 [CAtlException](../../atl/reference/catlexception-class.md) 。 此函数通常用于返回自动化的字符串。

通常，如果将此字符串作为参数传递给 COM 函数 `[in]` ，则这需要调用方释放字符串。 这可以通过使用 [SysFreeString](/windows/win32/api/oleauto/nf-oleauto-sysfreestring)来完成，如 Windows SDK 中所述。 有关详细信息，请参阅为 [BSTR 分配和释放内存](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)。

有关 Windows 中的 OLE 分配函数的详细信息，请参阅 Windows SDK 中的 [SysAllocString](/windows/win32/api/oleauto/nf-oleauto-sysallocstring) 。

### <a name="example"></a>示例

以下示例演示了 `CStringT::AllocSysString` 的用法。

[!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]

## <a name="cstringtansitooem"></a><a name="ansitooem"></a> `CStringT::AnsiToOem`

将此对象中的所有字符 **`CStringT`** 从 ANSI 字符集转换为 OEM 字符集。

```cpp
void AnsiToOem();
```

### <a name="remarks"></a>备注

如果定义了，则函数不可用 `_UNICODE` 。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

## <a name="cstringtappendformat"></a><a name="appendformat"></a> `CStringT::AppendFormat`

将格式化的数据追加到现有 **`CStringT`** 对象。

```cpp
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```

### <a name="parameters"></a>参数

*`pszFormat`*\
格式控制字符串。

*`nFormatID`*\
字符串资源标识符，其中包含格式控制字符串。

*`argument`*\
可选参数。

### <a name="remarks"></a>备注

此函数在中设置并追加一系列字符和值 **`CStringT`** 。 如果根据中的相应格式规范 *`pszFormat`* 或从标识的字符串资源中转换并追加任何) ，则每个可选参数 (*`nFormatID`* 。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

## <a name="cstringtcollate"></a><a name="collate"></a> `CStringT::Collate`

使用一般文本函数比较两个字符串 `_tcscoll` 。

```cpp
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>参数

*`psz`*\
用于比较的另一个字符串。

### <a name="return-value"></a>返回值

如果字符串相同，则为零; 如果此对象 **`CStringT`** 小于，则 < 0; *`psz`* 如果此对象大于，则为 > 0 **`CStringT`** *`psz`* 。

### <a name="remarks"></a>备注

`_tcscoll`在 TCHAR 中定义的一般文本函数。H，映射到 `strcoll` 、 `wcscoll` 或，具体取决于在 `_mbscoll` 编译时定义的字符集。 每个函数根据当前使用的代码页对字符串执行区分大小写的比较。 有关详细信息，请参阅 [strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)。

## <a name="cstringtcollatenocase"></a><a name="collatenocase"></a> `CStringT::CollateNoCase`

使用一般文本函数比较两个字符串 `_tcscoll` 。

```cpp
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>参数

*`psz`*\
用于比较的另一个字符串。

### <a name="return-value"></a>返回值

如果字符串相同 (忽略大小写) ，则为零; 如果此 **`CStringT`** 对象小于 *`psz`* (忽略大小写) ，则 < 0; 如果此 **`CStringT`** 对象大于 *`psz`* > 忽略大小写 (，则为) 0。

### <a name="remarks"></a>备注

`_tcscoll`在 TCHAR 中定义的一般文本函数。H，映射到 `stricoll` 、 `wcsicoll` 或，具体取决于在 `_mbsicoll` 编译时定义的字符集。 每个函数根据当前使用的代码页，对字符串执行不区分大小写的比较。 有关详细信息，请参阅 [strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]

## <a name="cstringtcompare"></a><a name="compare"></a> `CStringT::Compare`

比较区分大小写)  (两个字符串。

```cpp
int Compare(PCXSTR psz) const;
```

### <a name="parameters"></a>参数

*`psz`*\
用于比较的另一个字符串。

### <a name="return-value"></a>返回值

如果字符串相同，则为零; 如果此对象 **`CStringT`** 小于，则 < 0; *`psz`* 如果此对象大于，则为 > 0 **`CStringT`** *`psz`* 。

### <a name="remarks"></a>备注

`_tcscmp`在 TCHAR 中定义的一般文本函数。H，映射到 `strcmp` 、 `wcscmp` 或，具体取决于在 `_mbscmp` 编译时定义的字符集。 每个函数对字符串执行区分大小写的比较，不受区域设置的影响。 有关详细信息，请参阅 [strcmp、wcscmp、_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)。

如果字符串包含嵌入的 null 值，则在进行比较时，字符串将被视为在第一个嵌入的 null 字符处截断。

### <a name="example"></a>示例

以下示例演示了 `CStringT::Compare` 的用法。

[!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]

## <a name="cstringtcomparenocase"></a><a name="comparenocase"></a> `CStringT::CompareNoCase`

比较不区分大小写的)  (两个字符串。

```cpp
int CompareNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>参数

*`psz`*\
用于比较的另一个字符串。

### <a name="return-value"></a>返回值

如果字符串相同 (忽略大小写) ，则为零; 如果此 **`CStringT`** 对象小于 *`psz`* (忽略大小写) ，则 <0; 如果此 **`CStringT`** 对象大于 *`psz`* >忽略大小写 (，则为) 0。

### <a name="remarks"></a>备注

`_tcsicmp`在 TCHAR 中定义的一般文本函数。H，映射到 `_stricmp` `_wcsicmp` 或 `_mbsicmp` ，具体取决于在编译时定义的字符集。 每个函数对字符串执行不区分大小写的比较。 比较取决于区域设置的 LC_CTYPE 方面，但不 LC_COLLATE。 有关详细信息，请参阅 [_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]

## <a name="cstringtcstringt"></a><a name="cstringt"></a> `CStringT::CStringT`

构造 **`CStringT`** 对象。

```cpp
CStringT() throw() :
    CThisSimpleString(StringTraits::GetDefaultManager());

explicit CStringT(IAtlStringMgr* pStringMgr) throw() :
    CThisSimpleString( pStringMgr);

CStringT(const VARIANT& varSrc);

CStringT(const VARIANT& varSrc, IAtlStringMgr* pStringMgr);

CStringT(const CStringT& strSrc) :
    CThisSimpleString( strSrc);

operator CSimpleStringT<
                    BaseType,
                    !_CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>
                    :: c_bIsMFCDLLTraits> &()

template <bool bMFCDLL>
CStringT(const CSimpleStringT<BaseType, bMFCDLL>& strSrc) :
    CThisSimpleString( strSrc);

template <class SystemString>
CStringT(SystemString^ pString) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(const YCHAR* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(LPCSTR pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CStringT(LPCWSTR pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CSTRING_EXPLICIT CStringT(const unsigned char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

/*CSTRING_EXPLICIT*/ CStringT(char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(unsigned char* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(wchar_t* pszSrc) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const unsigned char* pszSrc, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);

CSTRING_EXPLICIT CStringT(char ch, int nLength = 1) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CSTRING_EXPLICIT CStringT(wchar_t ch, int nLength = 1) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pch, int nLength) :
    CThisSimpleString( pch, nLength, StringTraits::GetDefaultManager());

CStringT(const YCHAR* pch, int nLength) :
    CThisSimpleString( StringTraits::GetDefaultManager());

CStringT(const XCHAR* pch, int nLength, AtlStringMgr* pStringMgr) :
    CThisSimpleString( pch, nLength, pStringMgr);

CStringT(const YCHAR* pch, int nLength, IAtlStringMgr* pStringMgr) :
    CThisSimpleString( pStringMgr);
```

### <a name="parameters"></a>参数

*`pch`*\
指向长度为 *nLength*、不是以 null 结尾的字符数组的指针。

*`nLength`*\
*Pch* 中字符数的计数。

*`ch`*\
单个字符。

*`pszSrc`*\
要复制到此对象中的以 null 值结束的字符串 **`CStringT`** 。

*`pStringMgr`*\
指向对象的内存管理器的指针 **`CStringT`** 。 有关 `IAtlStringMgr` 和内存管理的详细信息 **`CStringT`** ，请参阅 [CStringT 的内存管理](../../atl-mfc-shared/memory-management-with-cstringt.md)。

*`strSrc`*\
**`CStringT`** 要复制到此对象中的现有对象 **`CStringT`** 。 有关和的详细 `CThisString` 信息 `CThisSimpleString` ，请参阅 "备注" 部分。

*`varSrc`*\
要复制到此对象中的 variant 对象 **`CStringT`** 。

*`BaseType`*\
字符串类的字符类型。 可以是以下值之一：

**`char`** 为 ANSI 字符串)  (。

**`wchar_t`**)  (Unicode 字符串。

`TCHAR` 为 ANSI 和 Unicode 字符串)  (。

*`bMFCDLL`*\
布尔值，指定项目是 MFC DLL (`TRUE`) 还是不 (`FALSE`) 。

*`SystemString`*\
必须为 `System::String` ，且项目必须用编译 `/clr` 。

*`pString`*\
对象的句柄 **`CStringT`** 。

### <a name="remarks"></a>备注

由于构造函数将输入数据复制到新分配的存储中，因此可能会导致内存异常。 其中一些构造函数充当转换函数。 例如，您可以用来替换 **`LPTSTR`** **`CStringT`** 对象的预期位置。

- **`CStringT`** ( `LPCSTR` `lpsz` ) ： **`CStringT`** 从 ANSI 字符串构造 Unicode。 你还可以使用此构造函数加载字符串资源，如以下示例中所示。

- `CStringT(``LPCWSTR` `lpsz` ) ： **`CStringT`** 从 Unicode 字符串构造。

- **`CStringT`** ( `const unsigned char*` `psz` ) ：允许构造从指向的 **`CStringT`** 指针 **`unsigned char`** 。

> [!NOTE]
> 定义 `_CSTRING_DISABLE_NARROW_WIDE_CONVERSION` 宏以关闭 ANSI 和 Unicode 字符串之间的隐式字符串转换。 宏从支持转换的编译构造函数中排除。

*`strSrc`* 参数可以是 **`CStringT`** 或 `CThisSimpleString` 对象。 对于 **`CStringT`** ，请使用其默认实例之一 (`CString` 、 `CStringA` 或 `CStringW`) ; 对于 `CThisSimpleString` ，请使用 **`this`** 指针。 `CThisSimpleString` 声明 [CSimpleStringT 类](../../atl-mfc-shared/reference/csimplestringt-class.md)的实例，该类是具有比类更少的内置功能的较小字符串类 **`CStringT`** 。

重载运算符 `CSimpleStringT<>&()` **`CStringT`** 从声明构造对象 `CSimpleStringT` 。

> [!NOTE]
> 尽管可以创建 **`CStringT`** 包含嵌入的 null 字符的实例，但是我们建议您不要这样做。 对 **`CStringT`** 包含嵌入的 null 字符的对象调用方法和运算符可能会产生意外的结果。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

## <a name="cstringtcstringt"></a><a name="_dtorcstringt"></a> `CStringT::~CStringT`

销毁 **`CStringT`** 对象。

```cpp
~CStringT() throw();
```

### <a name="remarks"></a>备注

销毁 **`CStringT`** 对象。

## <a name="cstringtdelete"></a><a name="delete"></a> `CStringT::Delete`

从字符串中删除以给定索引处的字符开头的一个或多个字符。

```cpp
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>参数

*`iIndex`*\
要删除的对象中的第一个字符的从零开始的索引 **`CStringT`** 。

*`nCount`*\
要删除的字符数。

### <a name="return-value"></a>返回值

已更改的字符串的长度。

### <a name="remarks"></a>备注

如果 *`nCount`* 比字符串长，则将删除字符串的其余部分。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]

```Output
Before: Soccer is best,
    but hockey is quicker!
After: Soccer best,
    but hockey is quicker!
```

## <a name="cstringtfind"></a><a name="find"></a> `CStringT::Find`

在此字符串中搜索字符或子字符串的第一个匹配项。

```cpp
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```

### <a name="parameters"></a>参数

*`pszSub`*\
要搜索的子字符串。

*`iStart`*\
要开始搜索的字符串中的字符的索引，或者为0（从开头开始）。

*`ch`*\
要搜索的单个字符。

### <a name="return-value"></a>返回值

此对象中与请求的子字符串匹配的第一个字符的从零开始的索引 **`CStringT`** ; 如果未找到子字符串或字符，则为-1。

### <a name="remarks"></a>备注

重载函数以接受 (类似于运行时函数 `strchr`) 和字符串 (类似于) 的单个字符 `strstr` 。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]

## <a name="cstringtfindoneof"></a><a name="findoneof"></a> `CStringT::FindOneOf`

在此字符串中搜索与中包含的任何字符相匹配的第一个字符 *`pszCharSet`* 。

```cpp
int FindOneOf(PCXSTR pszCharSet) const throw();
```

### <a name="parameters"></a>参数

*`pszCharSet`*\
包含匹配字符的字符串。

### <a name="return-value"></a>返回值

此字符串中的第一个字符的从零开始的索引 *`pszCharSet`* ; 如果没有匹配项，则为-1。

### <a name="remarks"></a>备注

查找中任何字符的第一个匹配项 *`pszCharSet`* 。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]

## <a name="cstringtformat"></a><a name="format"></a> `CStringT::Format`

以 **`CStringT`** [sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) 将数据格式化为 C 样式字符数组的相同方式将格式化的数据写入。

```cpp
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```

### <a name="parameters"></a>参数

*`nFormatID`*\
字符串资源标识符，其中包含格式控制字符串。

*`pszFormat`*\
格式控制字符串。

*`argument`*\
可选参数。

### <a name="remarks"></a>备注

此函数在中设置和存储一系列字符和值 **`CStringT`** 。 如果根据中的相应格式规范 *`pszFormat`* 或从标识的字符串资源转换和输出任何) ，则每个可选参数 (*`nFormatID`* 。

如果字符串对象本身作为参数提供给，则调用将失败 `Format` 。 例如，以下代码将导致不可预知的结果：

[!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]

有关详细信息，请参阅[格式规范语法：printf 和 wprintf 函数](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]

## <a name="cstringtformatmessage"></a><a name="formatmessage"></a> `CStringT::FormatMessage`

设置消息字符串的格式。

```cpp
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```

### <a name="parameters"></a>参数

*`nFormatID`*\
包含未格式化消息文本的字符串资源标识符。

*`pszFormat`*\
指向格式控制字符串。 系统会对其进行扫描，以相应地进行插入和格式设置。 格式字符串与运行时函数 *printf* 样式的格式字符串类似，只是它允许以任意顺序插入参数。

*`argument`*\
可选参数。

### <a name="remarks"></a>备注

函数要求将消息定义作为输入。 消息定义由 *`pszFormat`* 和标识的字符串资源确定 *`nFormatID`* 。 函数将带格式的消息文本复制到 **`CStringT`** 对象，并在请求时处理任何嵌入的插入序列。

> [!NOTE]
> `FormatMessage` 尝试为新格式化的字符串分配系统内存。 如果此尝试失败，则会自动引发内存异常。

每个插入必须在或参数后面都有相应的参数 *`pszFormat`* *`nFormatID`* 。 在消息文本中，支持将多个转义序列动态格式化消息。 有关详细信息，请参阅 Windows SDK 中的 Windows [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) 函数。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]

## <a name="cstringtformatmessagev"></a><a name="formatmessagev"></a> `CStringT::FormatMessageV`

使用变量参数列表设置消息字符串的格式。

```cpp
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```

### <a name="parameters"></a>参数

*`pszFormat`*\
指向格式控制字符串。 系统会对其进行扫描，以相应地进行插入和格式设置。 格式字符串与运行时函数 `printf` 样式格式字符串类似，只是它允许以任意顺序插入参数。

*`pArgList`*\
指向参数列表的指针。

### <a name="remarks"></a>备注

函数需要消息定义作为输入，由确定 *`pszFormat`* 。 函数将带格式的消息文本和参数的变量列表复制到 **`CStringT`** 对象，并在请求时处理任何嵌入的插入序列。

> [!NOTE]
> `FormatMessageV` 调用 [CStringT：： FormatMessage](#formatmessage)，它尝试为新格式化的字符串分配系统内存。 如果此尝试失败，则会自动引发内存异常。

有关详细信息，请参阅 Windows SDK 中的 Windows [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) 函数。

## <a name="cstringtformatv"></a><a name="formatv"></a> `CStringT::FormatV`

使用变量参数列表设置消息字符串的格式。

```cpp
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>参数

*`pszFormat`*\
指向格式控制字符串。 系统会对其进行扫描，以相应地进行插入和格式设置。 格式字符串与运行时函数 `printf` 样式格式字符串类似，只是它允许以任意顺序插入参数。

*`args`*\
指向参数列表的指针。

### <a name="remarks"></a>备注

**`CStringT`** 使用将 `vsprintf_s` 数据格式化为 C 样式字符数组的相同方式将格式化字符串和变量的变量列表写入字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]

## <a name="cstringtgetenvironmentvariable"></a><a name="getenvironmentvariable"></a> `CStringT::GetEnvironmentVariable`

将字符串设置为指定环境变量的值。

```cpp
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```

### <a name="parameters"></a>参数

*`pszVar`*\
指向以 null 结尾的字符串的指针，该字符串指定环境变量。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

从调用进程的环境块中检索指定变量的值。 值的格式为以 null 结尾的字符。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]

## <a name="cstringtinsert"></a><a name="insert"></a> `CStringT::Insert`

在字符串中的给定索引处插入单个字符或子字符串。

```cpp
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```

### <a name="parameters"></a>参数

*`iIndex`*\
要在其之前插入的字符的索引。

*`psz`*\
指向要插入的子字符串的指针。

*`ch`*\
要插入的字符。

### <a name="return-value"></a>返回值

已更改的字符串的长度。

### <a name="remarks"></a>备注

*`iIndex`* 参数标识将移动的第一个字符，以便为字符或子字符串腾出空间。 如果 *nIndex* 为零，则将在整个字符串之前进行插入。 如果 *nIndex* 大于字符串的长度，则该函数将连接当前字符串和或提供的新材料 *`ch`* *`psz`* 。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

## <a name="cstringtleft"></a><a name="left"></a> `CStringT::Left`

从此对象中提取最左边的 *`nCount`* 字符 **`CStringT`** 并返回提取的子字符串的副本。

```cpp
CStringT Left(int nCount) const;
```

### <a name="parameters"></a>参数

*`nCount`*\
要从此对象中提取的字符数 **`CStringT`** 。

### <a name="return-value"></a>返回值

一个 **`CStringT`** 对象，该对象包含指定范围内的字符的副本。 返回的 **`CStringT`** 对象可能为空。

### <a name="remarks"></a>备注

如果 *`nCount`* 超过字符串长度，则提取整个字符串。 `Left` 类似于 Basic `Left` 函数。

对于 (MBCS) 的多字节字符集，将 *`nCount`* 每个8位序列视为一个字符，以便 *`nCount`* 返回多字节字符的数目乘以2。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

## <a name="cstringtloadstring"></a><a name="loadstring"></a> `CStringT::LoadString`

将 Windows 字符串资源（由 *nID* 标识）读入现有 **`CStringT`** 对象。

```cpp
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```

### <a name="parameters"></a>参数

*`hInstance`*\
模块实例的句柄。

*`nID`*\
Windows 字符串资源 ID。

*`wLanguageID`*\
字符串资源的语言。

### <a name="return-value"></a>返回值

如果资源加载成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

使用指定的语言 (*wLanguage*) 从指定的模块 (*hInstance*) 中加载字符串资源 (*nID*) 。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]

## <a name="cstringtmakelower"></a><a name="makelower"></a> `CStringT::MakeLower`

将 **`CStringT`** 对象转换为小写字符串。

```cpp
CStringT& MakeLower();
```

### <a name="return-value"></a>返回值

生成的小写字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

## <a name="cstringtmakereverse"></a><a name="makereverse"></a> `CStringT::MakeReverse`

反转对象中字符的顺序 **`CStringT`** 。

```cpp
CStringT& MakeReverse();
```

### <a name="return-value"></a>返回值

生成的反向字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

## <a name="cstringtmakeupper"></a><a name="makeupper"></a> `CStringT::MakeUpper`

将 **`CStringT`** 对象转换为大写字符串。

```cpp
CStringT& MakeUpper();
```

### <a name="return-value"></a>返回值

生成的大写字符串。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

## <a name="cstringtmid"></a><a name="mid"></a> `CStringT::Mid`

从此对象中提取长度为的子字符串 *`nCount`* **`CStringT`** ，从位置 *`iFirst`* (从零开始) 。

```cpp
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const;
```

### <a name="parameters"></a>参数

*`iFirst`*\
此 **`CStringT`** 对象中要包含在提取的子字符串中的第一个字符的从零开始的索引。

*`nCount`*\
要从此对象中提取的字符数 **`CStringT`** 。 如果未提供此参数，则提取字符串的其余部分。

### <a name="return-value"></a>返回值

一个 **`CStringT`** 对象，该对象包含指定范围内的字符的副本。 返回的 **`CStringT`** 对象可能为空。

### <a name="remarks"></a>备注

函数返回提取的子字符串的副本。 `Mid` 类似于基本的 Mid 函数 (，只不过基本函数中的索引是从1开始的) 。

对于 (MBCS) 的多字节字符集， *`nCount`* 引用每个8位字符; 即，一个多字节字符中的前导和尾字节计为两个字符。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

## <a name="cstringtoemtoansi"></a><a name="oemtoansi"></a> `CStringT::OemToAnsi`

将此对象中的所有字符 **`CStringT`** 从 OEM 字符集转换为 ANSI 字符集。

```cppcpp
void OemToAnsi();
```

### <a name="remarks"></a>备注

如果定义了，则此函数不可用 `_UNICODE` 。

### <a name="example"></a>示例

请参阅 [CStringT：： AnsiToOem](#ansitooem)的示例。

## <a name="cstringtoperator-"></a><a name="operator_eq"></a> `CStringT::operator =`

将新值分配给字符串。

```cpp
CStringT& operator=(const CStringT& strSrc);

template<bool bMFCDLL>
CStringT& operator=(const CSimpleStringT<BaseType, bMFCDLL>& str);
CStringT& operator=(PCXSTR pszSrc);
CStringT& operator=(PCYSTR pszSrc);
CStringT& operator=(const unsigned char* pszSrc);
CStringT& operator=(XCHAR ch);
CStringT& operator=(YCHAR ch);
CStringT& operator=(const VARIANT& var);
```

### <a name="parameters"></a>参数

*`strSrc`*\
**`CStringT`** 要分配给此字符串的。

*`str`*\
对 `CThisSimpleString` 对象的引用。

*`bMFCDLL`*\
指定项目是否为 MFC DLL 的布尔值。

*`BaseType`*\
字符串基类型。

*`var`*\
要分配给此字符串的 variant 对象。

*`ch`*\
要分配给字符串的 ANSI 或 Unicode 字符。

*`pszSrc`*\
指向要分配的原始字符串的指针。

### <a name="remarks"></a>备注

赋值运算符接受另一个 **`CStringT`** 对象、字符指针或单个字符。 使用此运算符时，可能会出现内存异常，因为可以分配新的存储。

有关的信息 `CThisSimpleString` ，请参阅 [CStringT：： CStringT](#cstringt)的 "备注" 部分。

> [!NOTE]
> 尽管可以创建 **`CStringT`** 包含嵌入的 null 字符的实例，但是我们建议您不要这样做。 对 **`CStringT`** 包含嵌入的 null 字符的对象调用方法和运算符可能会产生意外的结果。

## <a name="cstringtoperator-"></a><a name="operator_add"></a> `CStringT::operator +`

连接两个字符串或一个字符和一个字符串。

```cpp
friend CStringT operator+(const CStringT& str1, const CStringT& str2);
friend CStringT operator+(const CStringT& str1, PCXSTR psz2);
friend CStringT operator+(PCXSTR psz1, const CStringT& str2,);
friend CStringT operator+(char ch1, const CStringT& str2,);
friend CStringT operator+(const CStringT& str1, char ch2);
friend CStringT operator+(const CStringT& str1, wchar_t ch2);
friend CStringT operator+(wchar_t ch1, const CStringT& str2,);
```

### <a name="parameters"></a>参数

*`ch1`*\
要与字符串连接的 ANSI 或 Unicode 字符。

*`ch2`*\
要与字符串连接的 ANSI 或 Unicode 字符。

*`str1`*\
**`CStringT`** 要与字符串或字符连接的。

*`str2`*\
**`CStringT`** 要与字符串或字符连接的。

*`psz1`*\
指向以 null 结尾的字符串的指针，该字符串与字符串或字符进行连接。

*`psz2`*\
一个指针，指向要与字符串或字符连接的字符串。

### <a name="remarks"></a>备注

函数有七种重载形式 `CStringT::operator+` 。 第一版连接两个现有 **`CStringT`** 对象。 接下来的两个连接 **`CStringT`** 对象和一个以 null 结尾的字符串。 接下来的两个将 **`CStringT`** 对象和一个 ANSI 字符连接起来。 最后两个将 **`CStringT`** 对象和 Unicode 字符连接起来。

> [!NOTE]
> 尽管可以创建 **`CStringT`** 包含嵌入的 null 字符的实例，但是我们建议您不要这样做。 对 **`CStringT`** 包含嵌入的 null 字符的对象调用方法和运算符可能会产生意外的结果。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_add_eq"></a> `CStringT::operator +=`

将字符连接到字符串的末尾。

```cpp
CStringT& operator+=(const CThisSimpleString& str);

template<bool bMFCDLL>
CStringT& operator+=(const const CSimpleStringT<BaseType, bMFCDLL>& str);

template<int t_nSize>
CStringT& operator+=(const CStaticString<XCHAR, t_nSize>& strSrc);
CStringT& operator+=(PCXSTR pszSrc);
CStringT& operator+=(PCYSTR pszSrc);
CStringT& operator+=(char ch);
CStringT& operator+=(unsigned char ch);
CStringT& operator+=(wchar_t ch);
CStringT& operator+=(const VARIANT& var);
```

### <a name="parameters"></a>参数

*`str`*\
对 `CThisSimpleString` 对象的引用。

*`bMFCDLL`*\
指定项目是否为 MFC DLL 的布尔值。

*`BaseType`*\
字符串基类型。

*`var`*\
要连接到此字符串的变量对象。

*`ch`*\
要与字符串连接的 ANSI 或 Unicode 字符。

*`pszSrc`*\
指向要连接的原始字符串的指针。

*`strSrc`*\
**`CStringT`** 要连接到此字符串的。

### <a name="remarks"></a>备注

运算符接受另一个 **`CStringT`** 对象、字符指针或单个字符。 当你使用此串联运算符时，可能会出现内存异常，因为可以为添加到此对象的字符分配新存储 **`CStringT`** 。

有关的信息 `CThisSimpleString` ，请参阅 [CStringT：： CStringT](#cstringt)的 "备注" 部分。

> [!NOTE]
> 尽管可以创建 **`CStringT`** 包含嵌入的 null 字符的实例，但是我们建议您不要这样做。 对 **`CStringT`** 包含嵌入的 null 字符的对象调用方法和运算符可能会产生意外的结果。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_eq_eq"></a> `CStringT::operator ==`

确定两个字符串是否逻辑上相等。

```cpp
friend bool operator==(const CStringT& str1, const CStringT& str2) throw();
friend bool operator==(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator==(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator==(const CStringT& str1, XCHAR ch2) throw();
friend bool operator==(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator==(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator==(XCHAR ch1, const CStringT& str2,) throw();
```

### <a name="parameters"></a>参数

*`ch1`*\
用于比较的 ANSI 或 Unicode 字符。

*`ch2`*\
用于比较的 ANSI 或 Unicode 字符。

*`str1`*\
**`CStringT`** 用于比较的。

*`str2`*\
**`CStringT`** 用于比较的。

*`psz1`*\
指向以 null 结尾的字符串的指针，用于比较。

*`psz2`*\
指向以 null 结尾的字符串的指针，用于比较。

### <a name="remarks"></a>备注

测试左侧的一个字符串或字符是否等于右侧的字符串或字符，并返回 `TRUE` 或 `FALSE` 相应地。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_neq"></a> `CStringT::operator !=`

确定两个字符串是否逻辑上不相等。

```cpp
friend bool operator!=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator!=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator!=(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator!=(const CStringT& str1, XCHAR ch2) throw();
friend bool operator!=(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator!=(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator!=(XCHAR ch1, const CStringT& str2,) throw();
```

### <a name="parameters"></a>参数

*`ch1`*\
要与字符串连接的 ANSI 或 Unicode 字符。

*`ch2`*\
要与字符串连接的 ANSI 或 Unicode 字符。

*`str1`*\
**`CStringT`** 用于比较的。

*`str2`*\
**`CStringT`** 用于比较的。

*`psz1`*\
指向以 null 结尾的字符串的指针，用于比较。

*`psz2`*\
指向以 null 结尾的字符串的指针，用于比较。

### <a name="remarks"></a>备注

测试左侧的一个字符串或字符是否不等于右侧的字符串或字符。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_lt"></a> `CStringT::operator <`

确定位于运算符左侧的字符串是否小于右侧的字符串的位置。

```cpp
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>参数

*`str1`*\
**`CStringT`** 用于比较的。

*`str2`*\
**`CStringT`** 用于比较的。

*`psz1`*\
指向以 null 结尾的字符串的指针，用于比较。

*`psz2`*\
指向以 null 结尾的字符串的指针，用于比较。

### <a name="remarks"></a>备注

字符串之间按字典比较的字符，按字符结束：

- 如果找到两个不相等的相应字符，则将比较结果作为字符串之间比较的结果。

- 如果找到的所有字符完全相同，但其中一个字符串的字符数要多于另一个字符串的字符数，则将较短的字符串视为小于较长的字符串。

- 如果找到的所有字符完全相同且字符串的字符数也相同，则这两个字符串视为相等。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_gt"></a> `CStringT::operator >`

确定位于运算符左侧的字符串是否大于右侧的字符串的位置。

```cpp
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>参数

*`str1`*\
**`CStringT`** 用于比较的。

*`str2`*\
**`CStringT`** 用于比较的。

*`psz1`*\
指向以 null 结尾的字符串的指针，用于比较。

*`psz2`*\
指向以 null 结尾的字符串的指针，用于比较。

### <a name="remarks"></a>备注

字符串之间按字典比较的字符，按字符结束：

- 如果找到两个不相等的相应字符，则将比较结果作为字符串之间比较的结果。

- 如果找到的所有字符完全相同，但其中一个字符串的字符数要多于另一个字符串的字符数，则将较短的字符串视为小于较长的字符串。

- 它没找到任何不相等的字符且字符串具有相同数量的字符，则字符串视为相等。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_lt_eq"></a> `CStringT::operator <=`

确定位于运算符左侧的字符串是否小于或等于右侧的字符串的位置。

```cpp
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>参数

*`str1`*\
**`CStringT`** 用于比较的。

*`str2`*\
**`CStringT`** 用于比较的。

*`psz1`*\
指向以 null 结尾的字符串的指针，用于比较。

*`psz2`*\
指向以 null 结尾的字符串的指针，用于比较。

### <a name="remarks"></a>备注

字符串之间按字典比较的字符，按字符结束：

- 如果找到两个不相等的相应字符，则将比较结果作为字符串之间比较的结果。

- 如果找到的所有字符完全相同，但其中一个字符串的字符数要多于另一个字符串的字符数，则将较短的字符串视为小于较长的字符串。

- 它没找到任何不相等的字符且字符串具有相同数量的字符，则字符串视为相等。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_gt_eq"></a> `CStringT::operator >=`

确定位于运算符左侧的字符串是否大于或等于右侧的字符串的字符串。

```cpp
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>参数

*`str1`*\
**`CStringT`** 用于比较的。

*`str2`*\
**`CStringT`** 用于比较的。

*`psz1`*\
指向用于比较的字符串的指针。

*`psz2`*\
指向用于比较的字符串的指针。

### <a name="remarks"></a>备注

字符串之间按字典比较的字符，按字符结束：

- 如果找到两个不相等的相应字符，则将比较结果作为字符串之间比较的结果。

- 如果找到的所有字符完全相同，但其中一个字符串的字符数要多于另一个字符串的字符数，则将较短的字符串视为小于较长的字符串。

- 它没找到任何不相等的字符且字符串具有相同数量的字符，则字符串视为相等。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]

## <a name="cstringtremove"></a><a name="remove"></a> `CStringT::Remove`

从字符串中移除指定字符的所有实例。

```cpp
int Remove(XCHAR chRemove);
```

### <a name="parameters"></a>参数

*`chRemove`*\
要从字符串中删除的字符。

### <a name="return-value"></a>返回值

从字符串中删除的字符数。 如果字符串未更改，则为零。

### <a name="remarks"></a>备注

字符的比较区分大小写。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]

## <a name="cstringtreplace"></a><a name="replace"></a> `CStringT::Replace`

有两个版本 `Replace` 。 第一个版本使用另一个子字符串替换子字符串的一个或多个副本。 两个子字符串都以 null 结尾。 第二个版本使用其他字符替换某个字符的一个或多个副本。 这两个版本对中存储的字符数据进行操作 **`CStringT`** 。

```cpp
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```

### <a name="parameters"></a>参数

*`pszOld`*\
指向要替换为以 null 结尾的字符串的指针 *`pszNew`* 。

*`pszNew`*\
指向以 null 结尾的字符串的指针，该字符串替换 *`pszOld`* 。

*`chOld`*\
要替换的字符 *`chNew`* 。

*`chNew`*\
替换的字符 *`chOld`* 。

### <a name="return-value"></a>返回值

返回字符或子字符串的被替换实例的数量; 如果字符串未更改，则返回零。

### <a name="remarks"></a>备注

`Replace` 可以更改字符串长度，因为 *`pszNew`* 和的 *`pszOld`* 长度不必相同，并且可以将旧子字符串的多个副本更改为新副本。 函数执行区分大小写的匹配。

实例的示例 **`CStringT`** 包括 `CString` 、 `CStringA` 和 `CStringW` 。

对于 `CStringA` ， `Replace` 使用 ANSI 或多字节 (MBCS) 字符。 对于 `CStringW` ， `Replace` 使用宽字符。

对于 `CString` ，根据是否定义了下表中的常量，在编译时选择字符数据类型。

|定义的常量|字符数据类型|
|----------------------|-------------------------|
|`_UNICODE`|宽字符|
|`_MBCS`|多字节字符|
|两者均未选中|单字节字符|
|推送、请求和匿名|Undefined|

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

## <a name="cstringtreversefind"></a><a name="reversefind"></a> `CStringT::ReverseFind`

在此 **`CStringT`** 对象中搜索字符的最后一个匹配项。

```cpp
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>参数

*`ch`*\
要搜索的字符。

### <a name="return-value"></a>返回值

此对象中与请求的字符匹配的最后一个字符的从零开始的索引 **`CStringT`** ; 如果未找到该字符，则为-1。

### <a name="remarks"></a>备注

函数类似于运行时函数 `strrchr` 。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

## <a name="cstringtright"></a><a name="right"></a> `CStringT::Right`

从该对象中提取最右) 个字符的最后一个 (， *`nCount`* **`CStringT`** 并返回提取的子字符串的副本。

```cpp
CStringT Right(int nCount) const;
```

### <a name="parameters"></a>参数

*`nCount`*\
要从此对象中提取的字符数 **`CStringT`** 。

### <a name="return-value"></a>返回值

一个 **`CStringT`** 对象，该对象包含指定范围内的字符的副本。 返回的 **`CStringT`** 对象可以为空。

### <a name="remarks"></a>备注

如果 *`nCount`* 超过字符串长度，则提取整个字符串。 `Right` 与基本 `Right` 函数 (相似，只不过基本函数中的索引从零开始) 。

对于 (MBCS) 的多字节字符集， *`nCount`* 引用每个8位字符; 即，一个多字节字符中的前导和尾字节计为两个字符。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

## <a name="cstringtsetsysstring"></a><a name="setsysstring"></a> `CStringT::SetSysString`

重新分配所指向的， **`BSTR`** *`pbstr`* 并将对象的内容复制 **`CStringT`** 到其中，包括 NULL 字符。

```cpp
BSTR SetSysString(BSTR* pbstr) const;
```

### <a name="parameters"></a>参数

*`pbstr`*\
指向字符串的指针。

### <a name="return-value"></a>返回值

新字符串。

### <a name="remarks"></a>备注

根据对象的内容，所 **`CStringT`** 引用的的值 **`BSTR`** *`pbstr`* 可以更改。 如果内存不足，则函数将引发 `CMemoryException` 。

此函数通常用于更改自动引用传递的字符串值。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]

## <a name="cstringtspanexcluding"></a><a name="spanexcluding"></a> `CStringT::SpanExcluding`

提取字符串中的字符（从第一个字符开始，该字符不在标识的字符集中） *`pszCharSet`* 。

```cpp
CStringT SpanExcluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>参数

*`pszCharSet`*\
解释为一组字符的字符串。

### <a name="return-value"></a>返回值

包含字符串中的字符的子字符串，从字符串中的第一个字符开始，到 (字符串中找到的第一个字符，以字符串中的第一个字符开始，并以字符串中的第一个字符 *`pszCharSet`* 结束 *`pszCharSet`* ，但不包括) 中找到的字符串中的第一个字符 *`pszCharSet`* 。 如果在字符串中找不到字符，则返回整个字符串 *`pszCharSet`* 。

### <a name="remarks"></a>备注

`SpanExcluding` 提取并返回 (字符的第一个匹配项中的第一个匹配项之后的所有字符 *`pszCharSet`* ，在字符串中后的字符 *`pszCharSet`* 和其后面的所有字符都不会以) 的形式返回。 如果 *`pszCharSet`* 在字符串中找不到任何字符，则 `SpanExcluding` 返回整个字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]

## <a name="cstringtspanincluding"></a><a name="spanincluding"></a> `CStringT::SpanIncluding`

从由标识的字符集中的第一个字符开始，提取字符串中的字符 *`pszCharSet`* 。

```cpp
CStringT SpanIncluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>参数

*`pszCharSet`*\
解释为一组字符的字符串。

### <a name="return-value"></a>返回值

包含字符串中的字符的子字符串 *`pszCharSet`* ，从字符串中的第一个字符开始，到在不在中的字符串中找到字符时结束 *`pszCharSet`* 。 `SpanIncluding` 如果字符串中的第一个字符不在指定的集中，则返回一个空的子字符串。

### <a name="remarks"></a>备注

如果字符串的第一个字符不在字符集中，则 `SpanIncluding` 返回一个空字符串。 否则，它将返回集中的连续字符序列。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]

## <a name="cstringttokenize"></a><a name="tokenize"></a> `CStringT::Tokenize`

查找目标字符串中的下一个标记

```cpp
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const;
```

### <a name="parameters"></a>参数

*`pszTokens`*\
包含标记分隔符的字符串。 这些分隔符的顺序并不重要。

*`iStart`*\
要开始搜索的从零开始的索引。

### <a name="return-value"></a>返回值

**`CStringT`** 包含当前标记值的对象。

### <a name="remarks"></a>备注

`Tokenize`函数查找目标字符串中的下一个标记。 *PszTokens* 中的字符集指定要查找的令牌的可能分隔符。 在对函数的每个调用 `Tokenize` 开始时 *`iStart`* ，将跳过前导分隔符并返回 **`CStringT`** 包含当前标记的对象，该对象是到下一个分隔符字符之前的字符字符串。 的值 *`iStart`* 更新为位于结束分隔符字符后的位置; 如果已到达字符串的末尾，则为-1。 通过一系列对的调用，可以将更多标记从目标字符串的其余部分中分离出来 `Tokenize` ，使用 *`iStart`* 跟踪在字符串中要读取下一个标记的位置。 当没有更多的标记时，该函数将返回一个空字符串，并 *`iStart`* 将设置为-1。

与 CRT 标记函数（如 [`strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l`](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md) ）不同， `Tokenize` 不会修改目标字符串。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]

此示例的输出如下所示：

```Output
Resulting Token: First
Resulting Token: Second
Resulting Token: Third
```

## <a name="cstringttrim"></a><a name="trim"></a> `CStringT::Trim`

剪裁字符串中的前导和尾随字符。

```cpp
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```

### <a name="parameters"></a>参数

*`chTarget`*\
要剪裁的目标字符。

*`pszTargets`*\
指向字符串的指针，该字符串包含要剪裁的目标字符。 将从对象中修整中字符的所有前导匹配项和尾随匹配项 *`pszTargets`* **`CStringT`** 。

### <a name="return-value"></a>返回值

返回修整后的字符串。

### <a name="remarks"></a>备注

删除下列一项的所有前导匹配项和尾随匹配项：

- 指定的字符 *`chTarget`* 。

- 在指定的字符串中找到的所有字符 *`pszTargets`* 。

- 白.

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]

此示例的输出如下所示：

```Output
Before: "******Soccer is best, but liquor is quicker!!!!!"
After : "Soccer is best, but liquor is quicker"
```

## <a name="cstringttrimleft"></a><a name="trimleft"></a> `CStringT::TrimLeft`

剪裁字符串中的前导字符。

```cpp
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```

### <a name="parameters"></a>参数

*`chTarget`*\
要剪裁的目标字符。

*`pszTargets`*\
指向字符串的指针，该字符串包含要剪裁的目标字符。 将从对象中修整中字符的所有前导匹配项 *`pszTargets`* **`CStringT`** 。

### <a name="return-value"></a>返回值

生成的剪裁字符串。

### <a name="remarks"></a>备注

删除下列一项的所有前导匹配项和尾随匹配项：

- 指定的字符 *`chTarget`* 。

- 在指定的字符串中找到的所有字符 *`pszTargets`* 。

- 白.

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]

## <a name="cstringttrimright"></a><a name="trimright"></a> `CStringT::TrimRight`

剪裁字符串中的尾随字符。

```cpp
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```

### <a name="parameters"></a>参数

*`chTarget`*\
要剪裁的目标字符。

*`pszTargets`*\
指向字符串的指针，该字符串包含要剪裁的目标字符。 将从对象中修整中字符的所有尾随匹配项 *`pszTargets`* **`CStringT`** 。

### <a name="return-value"></a>返回值

返回 **`CStringT`** 包含剪裁后的字符串的对象。

### <a name="remarks"></a>备注

删除以下其中一项的尾随次出现：

- 指定的字符 *`chTarget`* 。

- 在指定的字符串中找到的所有字符 *`pszTargets`* 。

- 白.

`CStringT& TrimRight(XCHAR chTarget)`版本接受一个字符参数，并从字符串数据的末尾删除该字符的所有副本 **`CStringT`** 。 它从字符串的末尾开始，到前面。 它在发现其他字符或用 **`CStringT`** 完了字符数据时停止。

`CStringT& TrimRight(PCXSTR pszTargets)`版本接受以 null 结尾的字符串，该字符串包含要搜索的所有不同字符。 它将删除对象中这些字符的所有副本 **`CStringT`** 。 它从字符串的末尾开始，到前面。 它在发现不在目标字符串中的字符时，或在用尽 **`CStringT`** 字符数据时停止。 它不会尝试将整个目标字符串匹配到末尾处的子字符串 **`CStringT`** 。

`CStringT& TrimRight()`版本不需要参数。 它会从字符串末尾裁剪任意尾随空格字符 **`CStringT`** 。 空格字符可以是换行符、空格或制表符。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)\
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)\
[CSimpleStringT 类](../../atl-mfc-shared/reference/csimplestringt-class.md)
