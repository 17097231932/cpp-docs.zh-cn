---
title: OLE DB 使用者模板的宏和全局函数
ms.date: 02/11/2019
f1_keywords:
- ATL.AtlTraceErrorRecords
- ATL::AtlTraceErrorRecords
- AtlTraceErrorRecords
- BEGIN_ACCESSOR
- BEGIN_ACCESSOR_MAP
- END_ACCESSOR
- END_ACCESSOR_MAP
- BEGIN_COLUMN_MAP
- BLOB_ENTRY
- BLOB_ENTRY_LENGTH
- BLOB_ENTRY_LENGTH_STATUS
- BLOB_ENTRY_STATUS
- BLOB_NAME
- BLOB_NAME_LENGTH
- BLOB_NAME_LENGTH_STATUS
- BLOB_NAME_STATUS
- BOOKMARK_ENTRY
- COLUMN_ENTRY
- COLUMN_ENTRY_EX
- COLUMN_ENTRY_LENGTH
- COLUMN_ENTRY_LENGTH_STATUS
- COLUMN_ENTRY_PS
- COLUMN_ENTRY_PS_LENGTH
- COLUMN_ENTRY_PS_LENGTH_STATUS
- COLUMN_ENTRY_PS_STATUS
- COLUMN_ENTRY_STATUS
- COLUMN_ENTRY_TYPE
- COLUMN_ENTRY_TYPE_SIZE
- COLUMN_NAME
- COLUMN_NAME_EX
- COLUMN_NAME_LENGTH
- COLUMN_NAME_LENGTH_STATUS
- COLUMN_NAME_PS
- COLUMN_NAME_PS_LENGTH
- COLUMN_NAME_PS_LENGTH_STATUS
- COLUMN_NAME_PS_STATUS
- COLUMN_NAME_STATUS
- COLUMN_NAME_TYPE
- COLUMN_NAME_TYPE_PS
- COLUMN_NAME_TYPE_SIZE
- COLUMN_NAME_TYPE_STATUS
- END_COLUMN_MAP
- DEFINE_COMMAND
- DEFINE_COMMAND_EX
- BEGIN_PARAM_MAP
- END_PARAM_MAP
- SET_PARAM_TYPE
helpviewer_keywords:
- OLE DB consumer templates, macros
- macros, OLE DB consumer template
- AtlTraceErrorRecords function
- BEGIN_ACCESSOR macro, syntax
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR_MAP macro
- END_ACCESSOR macro
- END_ACCESSOR_MAP macro
- BEGIN_COLUMN_MAP macro
- BLOB_ENTRY macro
- BLOB_ENTRY_LENGTH macro
- BLOB_ENTRY_LENGTH_STATUS macro
- BLOB_ENTRY_STATUS macro
- BLOB_NAME macro
- BLOB_NAME_LENGTH macro
- BLOB_NAME_LENGTH_STATUS macro
- BLOB_NAME_STATUS macro
- BOOKMARK_ENTRY macro
- COLUMN_ENTRY macro
- COLUMN_ENTRY_EX macro
- COLUMN_ENTRY_LENGTH macro
- COLUMN_ENTRY_LENGTH_STATUS macro
- COLUMN_ENTRY_PS macro
- COLUMN_ENTRY_PS_LENGTH macro
- COLUMN_ENTRY_PS_LENGTH_STATUS macro
- COLUMN_ENTRY_PS_STATUS macro
- COLUMN_ENTRY_STATUS macro
- COLUMN_ENTRY_TYPE macro
- COLUMN_ENTRY_TYPE_SIZE macro
- COLUMN_NAME macro
- COLUMN_NAME_EX macro
- COLUMN_NAME_LENGTH macro
- COLUMN_NAME_LENGTH_STATUS macro
- COLUMN_NAME_PS macro
- COLUMN_NAME_PS_LENGTH macro
- COLUMN_NAME_PS_LENGTH_STATUS macro
- COLUMN_NAME_PS_STATUS macro
- COLUMN_NAME_STATUS macro
- COLUMN_NAME_TYPE macro
- COLUMN_NAME_TYPE_PS macro
- COLUMN_NAME_TYPE_SIZE macro
- COLUMN_NAME_TYPE_STATUS macro
- END_COLUMN_MAP macro
- DEFINE_COMMAND macro
- DEFINE_COMMAND_EX macro
- BEGIN_PARAM_MAP macro
- END_PARAM_MAP macro
- SET_PARAM_TYPE macro
ms.assetid: 8765eb7b-32dd-407c-bacf-8890ef959837
ms.openlocfilehash: 60f642366589bb13b15665331a81d440322eb13f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504031"
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>OLE DB 使用者模板的宏和全局函数

OLE DB 使用者模板包括以下宏和全局函数：

## <a name="global-functions"></a>全局函数

| 名称 | 说明 |
|-|-|
|[AtlTraceErrorRecords](#atltraceerrorrecords)|如果返回错误，则将 OLE DB 错误记录信息转储到转储设备。|

## <a name="accessor-map-macros"></a>访问器映射宏

| 名称 | 说明 |
|-|-|
|[BEGIN_ACCESSOR](#begin_accessor)|标记访问器项的开头。|
|[BEGIN_ACCESSOR_MAP](#begin_accessor_map)|标记取值函数映射条目的开始。|
|[END_ACCESSOR](#end_accessor)|标记访问器项的结尾。|
|[END_ACCESSOR_MAP](#end_accessor_map)|标记访问器映射项的结尾。|

## <a name="column-map-macros"></a>列映射宏

| 名称 | 说明 |
|-|-|
|[BEGIN_COLUMN_MAP](#begin_column_map)|标记用户记录类中的列映射条目的开头。|
|[BLOB_ENTRY](#blob_entry)|用于将二进制大型对象绑定 (BLOB) 。|
|[BLOB_ENTRY_LENGTH](#blob_entry_length)|报告 BLOB 数据列的长度。|
|[BLOB_ENTRY_LENGTH_STATUS](#blob_entry_length_status)|报告 BLOB 数据列的长度和状态。|
|[BLOB_ENTRY_STATUS](#blob_entry_status)|报告 BLOB 数据列的状态。|
|[BLOB_NAME](#blob_name)|用于按列名称绑定二进制大型对象。|
|[BLOB_NAME_LENGTH](#blob_name_length)|报告 BLOB 数据列的长度。|
|[BLOB_NAME_LENGTH_STATUS](#blob_name_length_status)|报告 BLOB 数据列的长度和状态。|
|[BLOB_NAME_STATUS](#blob_name_status)|报告 BLOB 数据列的状态。|
|[BOOKMARK_ENTRY](#bookmark_entry)|表示行集上的书签条目。 书签项是一种特殊的列项。|
|[COLUMN_ENTRY](#column_entry)|表示对数据库中特定列的绑定。|
|[COLUMN_ENTRY_EX](#column_entry_ex)|表示对数据库中特定列的绑定。 支持 *类型*、 *长度*、 *精度*、 *小数位数*和 *状态* 参数。|
|[COLUMN_ENTRY_LENGTH](#column_entry_length)|表示对数据库中特定列的绑定。 支持 *length* 变量。|
|[COLUMN_ENTRY_LENGTH_STATUS](#column_entry_length_status)|表示对数据库中特定列的绑定。 支持 *状态* 和 *长度* 参数。|
|[COLUMN_ENTRY_PS](#column_entry_ps)|表示对数据库中特定列的绑定。 支持 *精度* 和 *小数位数* 参数。|
|[COLUMN_ENTRY_PS_LENGTH](#column_entry_ps_length)|表示对数据库中特定列的绑定。 支持 *长度* 变量、 *精度* 和 *小数位数* 参数。|
|[COLUMN_ENTRY_PS_LENGTH_STATUS](#column_entry_ps_length_status)|表示对数据库中特定列的绑定。 支持 *状态* 和 *长度* 变量、 *精度* 和 *小数位数* 参数。|
|[COLUMN_ENTRY_PS_STATUS](#column_entry_ps_status)|表示对数据库中特定列的绑定。 支持 *状态* 变量、 *精度* 和 *小数位数* 参数。|
|[COLUMN_ENTRY_STATUS](#column_entry_status)|表示对数据库中特定列的绑定。 支持 *状态* 变量。|
|[COLUMN_ENTRY_TYPE](#column_entry_type)|表示对数据库中特定列的绑定。 支持 *类型* 参数。|
|[COLUMN_ENTRY_TYPE_SIZE](#column_entry_type_size)|表示对数据库中特定列的绑定。 支持 *类型* 和 *大小* 参数。|
|[COLUMN_NAME](#column_name)|表示按名称绑定到数据库中的特定列。|
|[COLUMN_NAME_EX](#column_name_ex)|表示按名称绑定到数据库中的特定列。 支持指定的数据类型、大小、精度、小数位数、列长度和列状态。|
|[COLUMN_NAME_LENGTH](#column_name_length)|表示按名称绑定到数据库中的特定列。 支持列长度规范。|
|[COLUMN_NAME_LENGTH_STATUS](#column_name_length_status)|表示按名称绑定到数据库中的特定列。 支持列长度和状态的说明。|
|[COLUMN_NAME_PS](#column_name_ps)|表示按名称绑定到数据库中的特定列。 支持精度和小数位数规范。|
|[COLUMN_NAME_PS_LENGTH](#column_name_ps_length)|表示按名称绑定到数据库中的特定列。 支持精度、小数位数和列长度的规范。|
|[COLUMN_NAME_PS_LENGTH_STATUS](#column_name_ps_length_status)|表示按名称绑定到数据库中的特定列。 支持精度、小数位数、列长度和列状态的规范。|
|[COLUMN_NAME_PS_STATUS](#column_name_ps_status)|表示按名称绑定到数据库中的特定列。 支持精度、小数位数和列状态的规范。|
|[COLUMN_NAME_STATUS](#column_name_status)|表示按名称绑定到数据库中的特定列。 支持列状态的说明。|
|[COLUMN_NAME_TYPE](#column_name_type)|表示按名称绑定到数据库中的特定列。 支持数据类型的规范。|
|[COLUMN_NAME_TYPE_PS](#column_name_type_ps)|表示按名称绑定到数据库中的特定列。 支持数据类型、精度和小数位数的规范。|
|[COLUMN_NAME_TYPE_SIZE](#column_name_type_size)|表示按名称绑定到数据库中的特定列。 支持指定的数据类型和大小。|
|[COLUMN_NAME_TYPE_STATUS](#column_name_type_status)|表示按名称绑定到数据库中的特定列。 支持数据类型和列状态的说明。|
|[END_COLUMN_MAP](#end_column_map)|标记列映射条目的结尾。|

## <a name="command-macros"></a>命令宏

| 名称 | 说明 |
|-|-|
|[DEFINE_COMMAND](#define_command)|指定使用 [CCommand](../../data/oledb/ccommand-class.md) 类时将用于创建行集的命令。 仅接受与指定的应用程序类型匹配 (ANSI 或 Unicode) 的字符串类型。 建议使用 [DEFINE_COMMAND_EX](#define_command_ex) 而不是 DEFINE_COMMAND。|
|[DEFINE_COMMAND_EX](#define_command_ex)|指定使用 [CCommand](../../data/oledb/ccommand-class.md) 类时将用于创建行集的命令。 支持 ANSI 和 Unicode 应用程序。|

## <a name="parameter-map-macros"></a>参数映射宏

| 名称 | 说明 |
|-|-|
|[BEGIN_PARAM_MAP](#begin_param_map)|标记用户记录类中参数映射条目的开头。|
|[END_PARAM_MAP](#end_param_map)|标记参数映射项的结尾。|
|[SET_PARAM_TYPE](#set_param_type)|指定在 SET_PARAM_TYPE 宏之后 COLUMN_ENTRY 宏作为输入、输出或输入/输出。|

### <a name="atltraceerrorrecords"></a><a name="atltraceerrorrecords"></a> AtlTraceErrorRecords

如果返回错误，则将 OLE DB 错误记录信息转储到转储设备。

#### <a name="syntax"></a>语法

```cpp
inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);
```

#### <a name="parameters"></a>参数

*hErr*<br/>
中OLE DB 使用者模板成员函数返回的 HRESULT。

#### <a name="remarks"></a>注解

如果未 S_OK *hErr* ，则会将 `AtlTraceErrorRecords` OLE DB 错误记录信息转储到 "输出" 窗口的 " **调试** " 选项卡中 (转储设备或文件) 。 从提供程序中获取的错误记录信息包含行号、源、说明、帮助文件、上下文和每个错误记录条目的 GUID。 `AtlTraceErrorRecords` 仅在调试版本中转储此信息。 在发布版本中，它是一个被优化的空存根。有关详细信息，请参阅 [CDBErrorInfo 类](../../data/oledb/cdberrorinfo-class.md)。

### <a name="begin_accessor"></a><a name="begin_accessor"></a> BEGIN_ACCESSOR

标记访问器项的开头。

#### <a name="syntax"></a>语法

```cpp
BEGIN_ACCESSOR(num, bAuto)
```

#### <a name="parameters"></a>参数

*num*<br/>
中此访问器映射中访问器的零偏移量。

*bAuto*<br/>
中指定此访问器是自动访问器还是手动访问器。 如果为 **`true`** ，则访问器是自动的; 如果为 **`false`** ，则访问器是手动的。 自动访问器表示对移动操作获取数据。

#### <a name="remarks"></a>注解

如果行集上有多个访问器，则需要指定 BEGIN_ACCESSOR_MAP 并将 BEGIN_ACCESSOR 宏用于每个访问器。 BEGIN_ACCESSOR 宏用 END_ACCESSOR 宏完成。 BEGIN_ACCESSOR_MAP 宏用 END_ACCESSOR_MAP 宏完成。

#### <a name="example"></a>示例

请参阅 [BEGIN_ACCESSOR_MAP](#begin_accessor_map)。

### <a name="begin_accessor_map"></a><a name="begin_accessor_map"></a> BEGIN_ACCESSOR_MAP

标记取值函数映射条目的开始。

#### <a name="syntax"></a>语法

```cpp
BEGIN_ACCESSOR_MAP(x, num)
```

#### <a name="parameters"></a>参数

*x*<br/>
[in] 用户记录类的名称。

*num*<br/>
[in] 此取值函数映射中的取值函数数目。

#### <a name="remarks"></a>注解

如果行集上有多个访问器，则需要在开头指定 BEGIN_ACCESSOR_MAP，并对每个访问器使用 BEGIN_ACCESSOR 的宏。 BEGIN_ACCESSOR 宏用 END_ACCESSOR 宏完成。 访问器映射通过 END_ACCESSOR_MAP 宏完成。

如果在用户记录中只有一个取值函数，则使用宏 [BEGIN_COLUMN_MAP](#begin_column_map)。

#### <a name="example"></a>示例

```cpp
class CArtistsAccessor
{
public:
// Data Elements
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];
   short m_nAge;

// Output binding map
BEGIN_ACCESSOR_MAP(CArtistsAccessor, 2)
   BEGIN_ACCESSOR(0, true)
      COLUMN_ENTRY(1, m_szFirstName)
      COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false) // Not an auto accessor
      COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsAccessor, L" \
   SELECT \
      FirstName, \
      LastName, \
      Age \
      FROM Artists")
};
```

### <a name="end_accessor"></a><a name="end_accessor"></a> END_ACCESSOR

标记访问器项的结尾。

#### <a name="syntax"></a>语法

```cpp
END_ACCESSOR()
```

#### <a name="remarks"></a>备注

对于行集上的多个访问器，需要指定 BEGIN_ACCESSOR_MAP 并将 BEGIN_ACCESSOR 宏用于每个访问器。 BEGIN_ACCESSOR 宏用 END_ACCESSOR 宏完成。 BEGIN_ACCESSOR_MAP 宏用 END_ACCESSOR_MAP 宏完成。

#### <a name="example"></a>示例

请参阅 [BEGIN_ACCESSOR_MAP](#begin_accessor_map)。

### <a name="end_accessor_map"></a><a name="end_accessor_map"></a> END_ACCESSOR_MAP

标记访问器映射项的结尾。

#### <a name="syntax"></a>语法

```cpp
END_ACCESSOR_MAP()
```

#### <a name="remarks"></a>备注

对于行集上的多个访问器，需要指定 BEGIN_ACCESSOR_MAP 并将 BEGIN_ACCESSOR 宏用于每个访问器。 BEGIN_ACCESSOR 宏用 END_ACCESSOR 宏完成。 BEGIN_ACCESSOR_MAP 宏用 END_ACCESSOR_MAP 宏完成。

#### <a name="example"></a>示例

请参阅 [BEGIN_ACCESSOR_MAP](#begin_accessor_map)。

### <a name="begin_column_map"></a><a name="begin_column_map"></a> BEGIN_COLUMN_MAP

标记列映射条目的开头。

#### <a name="syntax"></a>语法

```cpp
BEGIN_COLUMN_MAP(x)
```

#### <a name="parameters"></a>参数

*x*<br/>
[in] 派生自 `CAccessor`的用户记录类的名称。

#### <a name="remarks"></a>注解

在行集上存在单个访问器的情况下使用此宏。 如果行集上有多个访问器，则使用 [BEGIN_ACCESSOR_MAP](#begin_accessor_map)。

BEGIN_COLUMN_MAP 宏用 END_COLUMN_MAP 宏完成。 当用户记录中只需要一个访问器时才使用此宏。

列对应行集中你希望绑定的字段。

#### <a name="example"></a>示例

以下是示例列和参数映射：

<!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->

### <a name="blob_entry"></a><a name="blob_entry"></a> BLOB_ENTRY

与 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 一起用于将二进制大型对象绑定 ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))) 。

#### <a name="syntax"></a>语法

```cpp
BLOB_ENTRY(nOrdinal, IID, flags, data)
```

#### <a name="parameters"></a>参数

*nOrdinal*<br/>
[in] 列号。

*IID*<br/>
中 `IDD_ISequentialStream`用于检索 BLOB 的接口 GUID，例如。

*flag*<br/>
中OLE 结构化存储模型定义的存储模式标志 (例如 `STGM_READ`) 。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="example"></a>示例

请参阅 [如何检索 BLOB？](../../data/oledb/retrieving-a-blob.md)。

### <a name="blob_entry_length"></a><a name="blob_entry_length"></a> BLOB_ENTRY_LENGTH

与 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 一起用于将二进制大型对象绑定 ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))) 。 与 [BLOB_ENTRY](#blob_entry)类似，只不过此宏还获取 BLOB 列的长度（以字节为单位）。

#### <a name="syntax"></a>语法

```cpp
BLOB_ENTRY_LENGTH(nOrdinal, IID, flags, data, length)
```

#### <a name="parameters"></a>参数

*nOrdinal*<br/>
[in] 列号。

*IID*<br/>
中 `IDD_ISequentialStream`用于检索 BLOB 的接口 GUID，例如。

*flag*<br/>
中OLE 结构化存储模型定义的存储模式标志 (例如 `STGM_READ`) 。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
弄 (实际的) BLOB 列长度（以字节为单位）。

#### <a name="example"></a>示例

请参阅 [如何检索 BLOB？](../../data/oledb/retrieving-a-blob.md)。

### <a name="blob_entry_length_status"></a><a name="blob_entry_length_status"></a> BLOB_ENTRY_LENGTH_STATUS

与 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 一起用于将二进制大型对象绑定 ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))) 。 与 [BLOB_ENTRY](#blob_entry)类似，不同之处在于此宏还获取 BLOB 列的长度和状态。

#### <a name="syntax"></a>语法

```cpp
BLOB_ENTRY_LENGTH_STATUS(
    nOrdinal,
    IID,
    flags,
    data,
    length,
    status )
```

#### <a name="parameters"></a>参数

*nOrdinal*<br/>
[in] 列号。

*IID*<br/>
中 `IDD_ISequentialStream`用于检索 BLOB 的接口 GUID，例如。

*flag*<br/>
中OLE 结构化存储模型定义的存储模式标志 (例如 `STGM_READ`) 。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
弄 (实际的) BLOB 列长度（以字节为单位）。

*status*<br/>
弄BLOB 数据列的状态。

#### <a name="example"></a>示例

请参阅 [如何检索 BLOB？](../../data/oledb/retrieving-a-blob.md)。

### <a name="blob_entry_status"></a><a name="blob_entry_status"></a> BLOB_ENTRY_STATUS

与 BEGIN_COLUMN_MAP 或 BEGIN_ACCESSOR_MAP 一起用于将二进制大型对象绑定 ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))) 。 与 [BLOB_ENTRY](#blob_entry)类似，只不过此宏还会获取 BLOB 列的状态。

#### <a name="syntax"></a>语法

```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)
```

#### <a name="parameters"></a>参数

*nOrdinal*<br/>
[in] 列号。

*IID*<br/>
中 `IDD_ISequentialStream`用于检索 BLOB 的接口 GUID，例如。

*flag*<br/>
中OLE 结构化存储模型定义的存储模式标志 (例如 `STGM_READ`) 。

*data*<br/>
[in] 用户记录中的对应数据成员。

*status*<br/>
弄BLOB 字段的状态。

#### <a name="example"></a>示例

请参阅 [如何检索 BLOB？](../../data/oledb/retrieving-a-blob.md)。

### <a name="blob_name"></a><a name="blob_name"></a> BLOB_NAME

与 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 一起用于将二进制大型对象绑定 ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))) 。 与 [BLOB_ENTRY](#blob_entry)类似，只不过此宏采用列名而不是列号。

#### <a name="syntax"></a>语法

```cpp
BLOB_NAME(pszName, IID, flags, data )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
中指向列名的指针。 名称必须是 Unicode 字符串。 您可以通过在名称前面放置一个 "L" 来实现此目的，例如： `L"MyColumn"` 。

*IID*<br/>
中 `IDD_ISequentialStream`用于检索 BLOB 的接口 GUID，例如。

*flag*<br/>
中OLE 结构化存储模型定义的存储模式标志 (例如 `STGM_READ`) 。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="example"></a>示例

请参阅 [如何检索 BLOB？](../../data/oledb/retrieving-a-blob.md)。

### <a name="blob_name_length"></a><a name="blob_name_length"></a> BLOB_NAME_LENGTH

与 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 一起用于将二进制大型对象绑定 ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))) 。 与 [BLOB_NAME](#blob_name)类似，不同之处在于此宏还获取 BLOB 数据列的长度（以字节为单位）。

#### <a name="syntax"></a>语法

```cpp
BLOB_NAME_LENGTH(pszName, IID, flags, data, length )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
中指向列名的指针。 名称必须是 Unicode 字符串。 您可以通过在名称前面放置一个 "L" 来实现此目的，例如： `L"MyColumn"` 。

*IID*<br/>
中 `IDD_ISequentialStream`用于检索 BLOB 的接口 GUID，例如。

*flag*<br/>
中OLE 结构化存储模型定义的存储模式标志 (例如 `STGM_READ`) 。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
弄 (实际的) BLOB 列长度（以字节为单位）。

### <a name="blob_name_length_status"></a><a name="blob_name_length_status"></a> BLOB_NAME_LENGTH_STATUS

与 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 一起用于将二进制大型对象绑定 ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))) 。 与 [BLOB_NAME](#blob_name)类似，不同之处在于此宏还获取 BLOB 数据列的长度和状态。

#### <a name="syntax"></a>语法

```cpp
BLOB_NAME_LENGTH_STATUS(pszName, IID, flags, data, length, status )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
中指向列名的指针。 名称必须是 Unicode 字符串。 您可以通过在名称前面放置一个 "L" 来实现此目的，例如： `L"MyColumn"` 。

*IID*<br/>
中 `IDD_ISequentialStream`用于检索 BLOB 的接口 GUID，例如。

*flag*<br/>
中OLE 结构化存储模型定义的存储模式标志 (例如 `STGM_READ`) 。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
弄 (实际的) BLOB 列长度（以字节为单位）。

*status*<br/>
弄BLOB 字段的状态。

### <a name="blob_name_status"></a><a name="blob_name_status"></a> BLOB_NAME_STATUS

与 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 一起用于将二进制大型对象绑定 ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))) 。 与 [BLOB_NAME](#blob_name)类似，只不过此宏还会获取 BLOB 数据列的状态。

#### <a name="syntax"></a>语法

```cpp
BLOB_NAME_STATUS(pszName, IID, flags, data, status )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
中指向列名的指针。 名称必须是 Unicode 字符串。 您可以通过在名称前面放置一个 "L" 来实现此目的，例如： `L"MyColumn"` 。

*IID*<br/>
中 `IDD_ISequentialStream`用于检索 BLOB 的接口 GUID，例如。

*flag*<br/>
中OLE 结构化存储模型定义的存储模式标志 (例如 `STGM_READ`) 。

*data*<br/>
[in] 用户记录中的对应数据成员。

*status*<br/>
弄BLOB 字段的状态。

### <a name="bookmark_entry"></a><a name="bookmark_entry"></a> BOOKMARK_ENTRY

绑定书签列。

#### <a name="syntax"></a>语法

```cpp
BOOKMARK_ENTRY(variable)
```

#### <a name="parameters"></a>参数

variable<br/>
中要绑定到书签列的变量。

#### <a name="example"></a>示例

```cpp
class CArtistsBookmark
{
public:
// Data Elements
   CBookmark<4> m_bookmark;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

// Output binding map
BEGIN_COLUMN_MAP(CArtistsBookmark)
   BOOKMARK_ENTRY(m_bookmark)
   COLUMN_ENTRY(1, m_nAge)
   COLUMN_ENTRY(2, m_szFirstName)
   COLUMN_ENTRY(3, m_szLastName)
END_COLUMN_MAP()

   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_BOOKMARKS, true);
   }

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsBookmark, L" \
   SELECT \
      Age, \
      FirstName, \
      LastName \
      FROM Artists")
};
```

有关详细信息，请参阅 [使用书签](using-bookmarks.md) 和 [CBookmark 类](../../data/oledb/cbookmark-class.md)。

### <a name="column_entry"></a><a name="column_entry"></a> COLUMN_ENTRY

表示行集中与行集中特定列之间的绑定。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY(nOrdinal, data)
```

#### <a name="parameters"></a>参数

请参阅*OLE DB 程序员参考*中的[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 。

*nOrdinal*<br/>
[in] 列号。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="remarks"></a>注解

COLUMN_ENTRY 宏用于以下位置：

- [BEGIN_COLUMN_MAP](#begin_column_map)和[END_COLUMN_MAP](#end_column_map)宏之间。

- [BEGIN_ACCESSOR](#begin_accessor)和[END_ACCESSOR](#end_accessor)宏之间。

- [BEGIN_PARAM_MAP](#begin_param_map)和[END_PARAM_MAP](#end_param_map)宏之间。

#### <a name="example"></a>示例

请参阅宏主题 [BEGIN_COLUMN_MAP](#begin_column_map) 和 [BEGIN_ACCESSOR_MAP](#begin_accessor_map)中的示例。

### <a name="column_entry_ex"></a><a name="column_entry_ex"></a> COLUMN_ENTRY_EX

表示行集上与数据库中的特定列的绑定。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY_EX(nOrdinal, wType, nLength, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>参数

请参阅*OLE DB 程序员参考*中的[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 。

*nOrdinal*<br/>
[in] 列号。

wType <br/>
中数据类型。

*nLength*<br/>
中数据大小（以字节为单位）。

*nPrecision*<br/>
中获取数据时使用的最大精度， *wType* 为 `DBTYPE_NUMERIC` 。 否则，将忽略此参数。

*nScale*<br/>
中获取数据时要使用的小数位数， *wType* 为 `DBTYPE_NUMERIC` 或 `DBTYPE_DECIMAL` 。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[in] 要绑定到列长度的变量。

*status*<br/>
[in] 要绑定到列变量的状态。

#### <a name="remarks"></a>注解

COLUMN_ENTRY_EX 宏用于以下位置：

- [BEGIN_COLUMN_MAP](#begin_column_map)和[END_COLUMN_MAP](#end_column_map)宏之间。

- [BEGIN_ACCESSOR](#begin_accessor)和[END_ACCESSOR](#end_accessor)宏之间。

- [BEGIN_PARAM_MAP](#begin_param_map)和[END_PARAM_MAP](#end_param_map)宏之间。

#### <a name="example"></a>示例

请参阅 [BOOKMARK_ENTRY](#bookmark_entry)。

### <a name="column_entry_length"></a><a name="column_entry_length"></a> COLUMN_ENTRY_LENGTH

表示行集上与数据库中的特定列的绑定。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY_LENGTH(nOrdinal, data, length)
```

#### <a name="parameters"></a>参数

请参阅*OLE DB 程序员参考*中的[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 。

*nOrdinal*<br/>
中列号，从1开始。 书签对应于列零。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[in] 要绑定到列长度的变量。

#### <a name="remarks"></a>注解

此宏支持 *length* 变量。 它在以下位置中使用：

- [BEGIN_COLUMN_MAP](#begin_column_map)和[END_COLUMN_MAP](#end_column_map)宏之间。

- [BEGIN_ACCESSOR](#begin_accessor)和[END_ACCESSOR](#end_accessor)宏之间。

- [BEGIN_PARAM_MAP](#begin_param_map)和[END_PARAM_MAP](#end_param_map)宏之间。

### <a name="column_entry_length_status"></a><a name="column_entry_length_status"></a> COLUMN_ENTRY_LENGTH_STATUS

表示行集上与数据库中的特定列的绑定。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY_LENGTH_STATUS(nOrdinal, data, length, status)
```

#### <a name="parameters"></a>参数

请参阅*OLE DB 程序员参考*中的[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 。

*nOrdinal*<br/>
[in] 列号。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[in] 要绑定到列长度的变量。

*status*<br/>
[in] 要绑定到列变量的状态。

#### <a name="remarks"></a>注解

当您要支持长度和状态变量时，请使用此宏。 它在以下位置中使用：

- [BEGIN_COLUMN_MAP](#begin_column_map)和[END_COLUMN_MAP](#end_column_map)宏之间。

- [BEGIN_ACCESSOR](#begin_accessor)和[END_ACCESSOR](#end_accessor)宏之间。

- [BEGIN_PARAM_MAP](#begin_param_map)和[END_PARAM_MAP](#end_param_map)宏之间。

### <a name="column_entry_ps"></a><a name="column_entry_ps"></a> COLUMN_ENTRY_PS

表示行集中与行集中特定列之间的绑定。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY_PS(nOrdinal, nPrecision, nScale, data)
```

#### <a name="parameters"></a>参数

请参阅*OLE DB 程序员参考*中的[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 。

*nOrdinal*<br/>
[in] 列号。

*nPrecision*<br/>
[in] 要绑定的列的最大精度。

*nScale*<br/>
[in] 要绑定的列的小数位数。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="remarks"></a>注解

允许您指定要绑定的列的精度和小数位数。 它在以下位置中使用：

- [BEGIN_COLUMN_MAP](#begin_column_map)和[END_COLUMN_MAP](#end_column_map)宏之间。

- [BEGIN_ACCESSOR](#begin_accessor)和[END_ACCESSOR](#end_accessor)宏之间。

- [BEGIN_PARAM_MAP](#begin_param_map)和[END_PARAM_MAP](#end_param_map)宏之间。

### <a name="column_entry_ps_length"></a><a name="column_entry_ps_length"></a> COLUMN_ENTRY_PS_LENGTH

表示行集上与数据库中的特定列的绑定。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY_PS_LENGTH(nOrdinal, nPrecision, nScale, data, length)
```

#### <a name="parameters"></a>参数

请参阅*OLE DB 程序员参考*中的[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 。

*nOrdinal*<br/>
中列号，从1开始。 书签对应于列零。

*nPrecision*<br/>
[in] 要绑定的列的最大精度。

*nScale*<br/>
[in] 要绑定的列的小数位数。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[in] 要绑定到列长度的变量。

#### <a name="remarks"></a>注解

允许您指定要绑定的列的精度和小数位数。 此宏支持 *length* 变量。 它在以下位置中使用：

- [BEGIN_COLUMN_MAP](#begin_column_map)和[END_COLUMN_MAP](#end_column_map)宏之间。

- [BEGIN_ACCESSOR](#begin_accessor)和[END_ACCESSOR](#end_accessor)宏之间。

- [BEGIN_PARAM_MAP](#begin_param_map)和[END_PARAM_MAP](#end_param_map)宏之间。

### <a name="column_entry_ps_length_status"></a><a name="column_entry_ps_length_status"></a> COLUMN_ENTRY_PS_LENGTH_STATUS

表示行集上与数据库中的特定列的绑定。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY_PS_LENGTH_STATUS(nOrdinal, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>参数

请参阅*OLE DB 程序员参考*中的[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 。

*nOrdinal*<br/>
[in] 列号。

*nPrecision*<br/>
[in] 要绑定的列的最大精度。

*nScale*<br/>
[in] 要绑定的列的小数位数。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[in] 要绑定到列长度的变量。

*status*<br/>
[in] 要绑定到列变量的状态。

#### <a name="remarks"></a>注解

允许您指定要绑定的列的精度和小数位数。 当您要支持长度和状态变量时，请使用此宏。 它在以下位置中使用：

- [BEGIN_COLUMN_MAP](#begin_column_map)和[END_COLUMN_MAP](#end_column_map)宏之间。

- [BEGIN_ACCESSOR](#begin_accessor)和[END_ACCESSOR](#end_accessor)宏之间。

- [BEGIN_PARAM_MAP](#begin_param_map)和[END_PARAM_MAP](#end_param_map)宏之间。

### <a name="column_entry_ps_status"></a><a name="column_entry_ps_status"></a> COLUMN_ENTRY_PS_STATUS

表示行集上与数据库中的特定列的绑定。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY_PS_STATUS(nOrdinal, nPrecision, nScale, data, status)
```

#### <a name="parameters"></a>参数

请参阅*OLE DB 程序员参考*中的[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 。

*nOrdinal*<br/>
[in] 列号。

*nPrecision*<br/>
[in] 要绑定的列的最大精度。

*nScale*<br/>
[in] 要绑定的列的小数位数。

*data*<br/>
[in] 用户记录中的对应数据成员。

*status*<br/>
[in] 要绑定到列变量的状态。

#### <a name="remarks"></a>注解

允许您指定要绑定的列的精度和小数位数。 此宏支持 *状态* 变量。 它在以下位置中使用：

- [BEGIN_COLUMN_MAP](#begin_column_map)和[END_COLUMN_MAP](#end_column_map)宏之间。

- [BEGIN_ACCESSOR](#begin_accessor)和[END_ACCESSOR](#end_accessor)宏之间。

- [BEGIN_PARAM_MAP](#begin_param_map)和[END_PARAM_MAP](#end_param_map)宏之间。

### <a name="column_entry_status"></a><a name="column_entry_status"></a> COLUMN_ENTRY_STATUS

表示行集上与数据库中的特定列的绑定。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY_STATUS(nOrdinal, data, status)
```

#### <a name="parameters"></a>参数

请参阅*OLE DB 程序员参考*中的[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 。

*nOrdinal*<br/>
[in] 列号。

*data*<br/>
[in] 用户记录中的对应数据成员。

*status*<br/>
[in] 要绑定到列变量的状态。

#### <a name="remarks"></a>注解

此宏支持 *状态* 变量。 它在以下位置中使用：

- [BEGIN_COLUMN_MAP](#begin_column_map)和[END_COLUMN_MAP](#end_column_map)宏之间。

- [BEGIN_ACCESSOR](#begin_accessor)和[END_ACCESSOR](#end_accessor)宏之间。

- [BEGIN_PARAM_MAP](#begin_param_map)和[END_PARAM_MAP](#end_param_map)宏之间。

### <a name="column_entry_type"></a><a name="column_entry_type"></a> COLUMN_ENTRY_TYPE

表示对数据库中特定列的绑定。 支持 *类型* 参数。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)
```

#### <a name="parameters"></a>参数

*nOrdinal*<br/>
[in] 列号。

wType <br/>
中列项的数据类型。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="remarks"></a>注解

此宏是 [COLUMN_ENTRY](#column_entry) 宏的专用变体，它提供指定数据类型的方法。

### <a name="column_entry_type_size"></a><a name="column_entry_type_size"></a> COLUMN_ENTRY_TYPE_SIZE

表示对数据库中特定列的绑定。 支持 *类型* 和 *大小* 参数。

#### <a name="syntax"></a>语法

```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)
```

#### <a name="parameters"></a>参数

*nOrdinal*<br/>
[in] 列号。

wType <br/>
中列项的数据类型。

*nLength*<br/>
中列项的大小（以字节为单位）。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="remarks"></a>注解

此宏是 [COLUMN_ENTRY](#column_entry) 宏的专用变体，它提供指定数据大小和类型的方法。

### <a name="column_name"></a><a name="column_name"></a> COLUMN_NAME

表示行集中与行集中特定列之间的绑定。 与 [COLUMN_ENTRY](#column_entry)类似，只不过此宏采用列名而不是列号。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME(pszName, data)
```

#### <a name="parameters"></a>参数

*pszName*<br/>
中指向列名的指针。 名称必须是 Unicode 字符串。 您可以通过在名称前面放置一个 "L" 来实现此目的，例如： `L"MyColumn"` 。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="remarks"></a>注解

COLUMN_NAME_ * 宏用于与 [COLUMN_ENTRY](#column_entry)相同的位置：

- [BEGIN_COLUMN_MAP](#begin_column_map)和[END_COLUMN_MAP](#end_column_map)宏之间。

- [BEGIN_ACCESSOR](#begin_accessor)和[END_ACCESSOR](#end_accessor)宏之间。

- [BEGIN_PARAM_MAP](#begin_param_map)和[END_PARAM_MAP](#end_param_map)宏之间。

### <a name="column_name_ex"></a><a name="column_name_ex"></a> COLUMN_NAME_EX

表示行集中与行集中特定列之间的绑定。 与 [COLUMN_NAME](#column_name)类似，不同之处在于，此宏还采用数据类型、大小、精度、小数位数、列长度和列状态。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
中指向列名的指针。 名称必须是 Unicode 字符串。 您可以通过在名称前面放置一个 "L" 来实现此目的，例如： `L"MyColumn"` 。

wType <br/>
中数据类型。

*nLength*<br/>
中数据大小（以字节为单位）。

*nPrecision*<br/>
中获取数据时使用的最大精度， *wType* 为 `DBTYPE_NUMERIC` 。 否则，将忽略此参数。

*nScale*<br/>
中获取数据时要使用的小数位数， *wType* 为 `DBTYPE_NUMERIC` 或 `DBTYPE_DECIMAL` 。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[in] 要绑定到列长度的变量。

*status*<br/>
[in] 要绑定到列变量的状态。

#### <a name="remarks"></a>注解

有关使用 COLUMN_NAME_ * 宏的信息，请参阅 [COLUMN_NAME](#column_name) 。

### <a name="column_name_length"></a><a name="column_name_length"></a> COLUMN_NAME_LENGTH

表示行集中与行集中特定列之间的绑定。 与 [COLUMN_NAME](#column_name)类似，不同之处在于此宏也采用列长度。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_LENGTH(pszName, data, length)
```

#### <a name="parameters"></a>参数

*pszName*<br/>
中指向列名的指针。 名称必须是 Unicode 字符串。 您可以通过在名称前面放置一个 "L" 来实现此目的，例如： `L"MyColumn"` 。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[in] 要绑定到列长度的变量。

#### <a name="remarks"></a>注解

有关使用 COLUMN_NAME_ * 宏的信息，请参阅 [COLUMN_NAME](#column_name) 。

### <a name="column_name_length_status"></a><a name="column_name_length_status"></a> COLUMN_NAME_LENGTH_STATUS

表示行集中与行集中特定列之间的绑定。 与 [COLUMN_NAME](#column_name)类似，只不过此宏还采用列长度和列状态。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_LENGTH_STATUS(pszName, data, length, status )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
中指向列名的指针。 名称必须是 Unicode 字符串。 您可以通过在名称前面放置一个 "L" 来实现此目的，例如： `L"MyColumn"` 。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[in] 要绑定到列长度的变量。

*status*<br/>
[in] 要绑定到列变量的状态。

#### <a name="remarks"></a>注解

有关使用 COLUMN_NAME_ * 宏的信息，请参阅 [COLUMN_NAME](#column_name) 。

### <a name="column_name_ps"></a><a name="column_name_ps"></a> COLUMN_NAME_PS

表示行集中与行集中特定列之间的绑定。 与 [COLUMN_NAME](#column_name)类似，不同之处在于此宏也需要精度和小数位数。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_PS(pszName, nPrecision, nScale, data )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
中指向列名的指针。 名称必须是 Unicode 字符串。 您可以通过在名称前面放置一个 "L" 来实现此目的，例如： `L"MyColumn"` 。

*nPrecision*<br/>
[in] 要绑定的列的最大精度。

*nScale*<br/>
[in] 要绑定的列的小数位数。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="remarks"></a>注解

有关使用 COLUMN_NAME_ * 宏的信息，请参阅 [COLUMN_NAME](#column_name) 。

### <a name="column_name_ps_length"></a><a name="column_name_ps_length"></a> COLUMN_NAME_PS_LENGTH

表示行集中与行集中特定列之间的绑定。 与 [COLUMN_NAME](#column_name)类似，不同之处在于此宏还采用精度、小数位数和列长度。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_PS_LENGTH(pszName, nPrecision, nScale, data, length )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
中指向列名的指针。 名称必须是 Unicode 字符串。 您可以通过在名称前面放置一个 "L" 来实现此目的，例如： `L"MyColumn"` 。

*nPrecision*<br/>
[in] 要绑定的列的最大精度。

*nScale*<br/>
[in] 要绑定的列的小数位数。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[in] 要绑定到列长度的变量。

#### <a name="remarks"></a>注解

有关使用 COLUMN_NAME_ * 宏的信息，请参阅 [COLUMN_NAME](#column_name) 。

### <a name="column_name_ps_length_status"></a><a name="column_name_ps_length_status"></a> COLUMN_NAME_PS_LENGTH_STATUS

表示行集中与行集中特定列之间的绑定。 与 [COLUMN_NAME](#column_name)类似，不同之处在于此宏也需要精度、小数位数、列长度和列状态。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
中指向列名的指针。 名称必须是 Unicode 字符串。 您可以通过在名称前面放置一个 "L" 来实现此目的，例如： `L"MyColumn"` 。

*nPrecision*<br/>
[in] 要绑定的列的最大精度。

*nScale*<br/>
[in] 要绑定的列的小数位数。

*data*<br/>
[in] 用户记录中的对应数据成员。

*length*<br/>
[in] 要绑定到列长度的变量。

*status*<br/>
[in] 要绑定到列变量的状态。

#### <a name="remarks"></a>注解

有关使用 COLUMN_NAME_ * 宏的信息，请参阅 [COLUMN_NAME](#column_name) 。

### <a name="column_name_ps_status"></a><a name="column_name_ps_status"></a> COLUMN_NAME_PS_STATUS

表示行集中与行集中特定列之间的绑定。 与 [COLUMN_NAME](#column_name)类似，不同之处在于此宏也需要精度、小数位数和列状态。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_PS_STATUS(pszName, nPrecision, nScale, data, status )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
中指向列名的指针。 名称必须是 Unicode 字符串。 您可以通过在名称前面放置一个 "L" 来实现此目的，例如： `L"MyColumn"` 。

*nPrecision*<br/>
[in] 要绑定的列的最大精度。

*nScale*<br/>
[in] 要绑定的列的小数位数。

*data*<br/>
[in] 用户记录中的对应数据成员。

*status*<br/>
[in] 要绑定到列变量的状态。

#### <a name="remarks"></a>注解

有关使用 COLUMN_NAME_ * 宏的信息，请参阅 [COLUMN_NAME](#column_name) 。

### <a name="column_name_status"></a><a name="column_name_status"></a> COLUMN_NAME_STATUS

表示行集中与行集中特定列之间的绑定。 与 [COLUMN_NAME](#column_name)类似，不同之处在于此宏也采用列状态。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_STATUS(pszName, data, status )
```

#### <a name="parameters"></a>参数

*pszName*<br/>
中指向列名的指针。 名称必须是 Unicode 字符串。 您可以通过在名称前面放置一个 "L" 来实现此目的，例如： `L"MyColumn"` 。

*data*<br/>
[in] 用户记录中的对应数据成员。

*status*<br/>
[in] 要绑定到列变量的状态。

#### <a name="remarks"></a>注解

有关使用 COLUMN_NAME_ * 宏的信息，请参阅 [COLUMN_NAME](#column_name) 。

### <a name="column_name_type"></a><a name="column_name_type"></a> COLUMN_NAME_TYPE

表示行集中与行集中特定列之间的绑定。 与 [COLUMN_NAME](#column_name)类似，只不过此宏还采用数据类型。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_TYPE(pszName, wType, data)
```

#### <a name="parameters"></a>参数

*pszName*<br/>
中指向列名的指针。 名称必须是 Unicode 字符串。 您可以通过在名称前面放置一个 "L" 来实现此目的，例如： `L"MyColumn"` 。

wType <br/>
中数据类型。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="remarks"></a>注解

有关使用 COLUMN_NAME_ * 宏的信息，请参阅 [COLUMN_NAME](#column_name) 。

### <a name="column_name_type_ps"></a><a name="column_name_type_ps"></a> COLUMN_NAME_TYPE_PS

表示行集中与行集中特定列之间的绑定。 与 [COLUMN_NAME](#column_name)类似，只不过此宏还采用数据类型、精度和小数位数。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_TYPE_PS(pszName, wType, nPrecision, nScale, data)
```

#### <a name="parameters"></a>参数

*pszName*<br/>
中指向列名的指针。 名称必须是 Unicode 字符串。 您可以通过在名称前面放置一个 "L" 来实现此目的，例如： `L"MyColumn"` 。

wType <br/>
中数据类型。

*nPrecision*<br/>
中获取数据时使用的最大精度， *wType* 为 `DBTYPE_NUMERIC` 。 否则，将忽略此参数。

*nScale*<br/>
中获取数据时要使用的小数位数， *wType* 为 `DBTYPE_NUMERIC` 或 `DBTYPE_DECIMAL` 。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="remarks"></a>注解

有关使用 COLUMN_NAME_ * 宏的信息，请参阅 [COLUMN_NAME](#column_name) 。

### <a name="column_name_type_size"></a><a name="column_name_type_size"></a> COLUMN_NAME_TYPE_SIZE

表示行集中与行集中特定列之间的绑定。 与 [COLUMN_NAME](#column_name)类似，只不过此宏还采用数据类型和大小。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_TYPE_SIZE(pszName, wType, nLength, data)
```

#### <a name="parameters"></a>参数

*pszName*<br/>
中指向列名的指针。 名称必须是 Unicode 字符串。 您可以通过在名称前面放置一个 "L" 来实现此目的，例如： `L"MyColumn"` 。

wType <br/>
中数据类型。

*nLength*<br/>
中数据大小（以字节为单位）。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="remarks"></a>注解

有关使用 COLUMN_NAME_ * 宏的信息，请参阅 [COLUMN_NAME](#column_name) 。

### <a name="column_name_type_status"></a><a name="column_name_type_status"></a> COLUMN_NAME_TYPE_STATUS

表示行集中与行集中特定列之间的绑定。 与 [COLUMN_NAME](#column_name)类似，只不过此宏还采用数据类型和列状态。

#### <a name="syntax"></a>语法

```cpp
COLUMN_NAME_TYPE_STATUS(pszName, wType, status, data)
```

#### <a name="parameters"></a>参数

*pszName*<br/>
中指向列名的指针。 名称必须是 Unicode 字符串。 您可以通过在名称前面放置一个 "L" 来实现此目的，例如： `L"MyColumn"` 。

wType <br/>
中数据类型。

*status*<br/>
[in] 要绑定到列变量的状态。

*data*<br/>
[in] 用户记录中的对应数据成员。

#### <a name="remarks"></a>注解

有关使用 COLUMN_NAME_ * 宏的信息，请参阅 [COLUMN_NAME](#column_name) 。

### <a name="end_column_map"></a><a name="end_column_map"></a> END_COLUMN_MAP

标记列映射条目的结尾。

#### <a name="syntax"></a>语法

```cpp
END_COLUMN_MAP()
```

#### <a name="remarks"></a>备注

它与行集上的单个访问器一起使用。 BEGIN_COLUMN_MAP 宏用 END_COLUMN_MAP 宏完成。

#### <a name="example"></a>示例

请参阅 [BEGIN_COLUMN_MAP](#begin_column_map)。

### <a name="define_command"></a><a name="define_command"></a> DEFINE_COMMAND

指定使用 [CCommand](../../data/oledb/ccommand-class.md) 类时将用于创建行集的命令。 仅接受与指定的应用程序类型匹配 (ANSI 或 Unicode) 的字符串类型。

> [!NOTE]
> 建议使用 [DEFINE_COMMAND_EX](#define_command_ex) 而不是 DEFINE_COMMAND。

#### <a name="syntax"></a>语法

```cpp
DEFINE_COMMAND(x, szCommand)
```

#### <a name="parameters"></a>参数

*x*<br/>
中用户记录 (命令) 类的名称。

*szCommand*<br/>
中当使用 [CCommand](../../data/oledb/ccommand-class.md)时，将用于创建行集的命令字符串。

#### <a name="remarks"></a>注解

如果未在 [CCommand：： Open](./ccommand-class.md#open) 方法中指定命令文本，则指定的命令字符串将用作默认值。

如果你将应用程序构建为 ANSI 或 Unicode 字符串（如果以 Unicode 形式生成应用程序），此宏将接受 ANSI 字符串。 建议使用 [DEFINE_COMMAND_EX](#define_command_ex) 而不是 DEFINE_COMMAND，因为前者接受 Unicode 字符串，而不考虑 ANSI 或 Unicode 应用程序类型。

#### <a name="example"></a>示例

请参阅 [BOOKMARK_ENTRY](#bookmark_entry)。

### <a name="define_command_ex"></a><a name="define_command_ex"></a> DEFINE_COMMAND_EX

指定使用 [CCommand](../../data/oledb/ccommand-class.md) 类时将用于创建行集的命令。 支持 Unicode 和 ANSI 应用程序。

#### <a name="syntax"></a>语法

```cpp
DEFINE_COMMAND_EX(x, wszCommand)
```

#### <a name="parameters"></a>参数

*x*<br/>
中用户记录 (命令) 类的名称。

*wszCommand*<br/>
中当使用 [CCommand](../../data/oledb/ccommand-class.md)时，将用于创建行集的命令字符串。

#### <a name="remarks"></a>注解

如果未在 [CCommand：： Open](./ccommand-class.md#open) 方法中指定命令文本，则指定的命令字符串将用作默认值。

此宏接受 Unicode 字符串，而不考虑应用程序类型。 由于此宏支持 Unicode 和 ANSI 应用程序，因此它优于 [DEFINE_COMMAND](#define_command) 。

#### <a name="example"></a>示例

请参阅 [BOOKMARK_ENTRY](#bookmark_entry)。

### <a name="begin_param_map"></a><a name="begin_param_map"></a> BEGIN_PARAM_MAP

标记参数映射项的开始。

#### <a name="syntax"></a>语法

```cpp
BEGIN_PARAM_MAP(x)
```

#### <a name="parameters"></a>参数

*x*<br/>
[in] 用户记录类的名称。

#### <a name="remarks"></a>注解

[命令](/previous-versions/windows/desktop/ms724608(v=vs.85))使用参数。

#### <a name="example"></a>示例

请参阅 [BEGIN_COLUMN_MAP](#begin_column_map) 宏的示例。

### <a name="end_param_map"></a><a name="end_param_map"></a> END_PARAM_MAP

标记参数映射项的结尾。

#### <a name="syntax"></a>语法

```cpp
END_PARAM_MAP()
```

#### <a name="example"></a>示例

请参阅 [BEGIN_PARAM_MAP](#begin_param_map) 宏的示例。

### <a name="set_param_type"></a><a name="set_param_type"></a> SET_PARAM_TYPE

指定在 SET_PARAM_TYPE 宏输入、输出或输入/输出之后 COLUMN_ENTRY 宏。

#### <a name="syntax"></a>语法

```cpp
SET_PARAM_TYPE(type)
```

#### <a name="parameters"></a>参数

type<br/>
[in] 要为参数设置的类型。

#### <a name="remarks"></a>注解

提供程序仅支持基础数据源支持的参数输入/输出类型。 该类型是一个或多个值的组合 `DBPARAMIO` (请参阅*OLE DB 程序员参考*) 中的[DBBINDING 结构](/previous-versions/windows/desktop/ms716845(v=vs.85))：

- `DBPARAMIO_NOTPARAM` 访问器没有参数。 通常情况下，将设置 `eParamIO` 为行访问器中的此值以提醒用户忽略参数。

- `DBPARAMIO_INPUT` 一个输入参数。

- `DBPARAMIO_OUTPUT` 输出参数。

- `DBPARAMIO_INPUT | DBPARAMIO_OUTPUT` 参数既是输入参数又是输出参数。

#### <a name="example"></a>示例

```cpp
class CArtistsProperty
{
public:
   short m_nReturn;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

BEGIN_PARAM_MAP(CArtistsProperty)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_nReturn)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_nAge)
END_PARAM_MAP()

BEGIN_COLUMN_MAP(CArtistsProperty)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
END_COLUMN_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsProperty, L" \
      { ? = SELECT Age FROM Artists WHERE Age < ? }")
};
```

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="see-also"></a>请参阅

[OLE DB 使用者模板的宏和全局函数](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)
