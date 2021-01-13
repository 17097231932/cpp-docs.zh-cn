---
description: 了解更多： CObject 类
title: CObject 类
ms.date: 1/12/2021
f1_keywords:
- CObject
- AFX/CObject
- AFX/CObject::CObject
- AFX/CObject::AssertValid
- AFX/CObject::Dump
- AFX/CObject::GetRuntimeClass
- AFX/CObject::IsKindOf
- AFX/CObject::IsSerializable
- AFX/CObject::Serialize
helpviewer_keywords:
- CObject [MFC], CObject
- CObject [MFC], AssertValid
- CObject [MFC], Dump
- CObject [MFC], GetRuntimeClass
- CObject [MFC], IsKindOf
- CObject [MFC], IsSerializable
- CObject [MFC], Serialize
ms.openlocfilehash: ba152a9cbbe6e2fa217d6c2e24d13ea48dd37c87
ms.sourcegitcommit: b51f79b5394e12cd90cb65c85cc01716f90bfc90
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/13/2021
ms.locfileid: "98167003"
---
# <a name="cobject-class"></a>`CObject` 类

Microsoft 基础类库中的主体基类。

## <a name="syntax"></a>语法

```cpp
class AFX_NOVTABLE CObject
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[`CObject::CObject`](#cobject)|默认构造函数。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[`CObject::AssertValid`](#assertvalid)|验证此对象的完整性。|
|[`CObject::Dump`](#dump)|生成此对象的诊断转储。|
|[`CObject::GetRuntimeClass`](#getruntimeclass)|返回 `CRuntimeClass` 与此对象的类相对应的结构。|
|[`CObject::IsKindOf`](#iskindof)|测试与给定类的此对象的关系。|
|[`CObject::IsSerializable`](#isserializable)|测试以确定此对象是否可以序列化。|
|[`CObject::Serialize`](#serialize)|从/向存档中加载或存储对象。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[`CObject::operator delete`](#operator_delete)|特殊 **`delete`** 运算符。|
|[`CObject::operator new`](#operator_new)|特殊 **`new`** 运算符。|

## <a name="remarks"></a>备注

它不仅可用作和等库类的根 `CFile` `CObList` ，还用作你编写的类的根。 `CObject` 提供基本服务，包括

- 序列化支持
- 运行时类信息
- 对象诊断输出
- 与集合类的兼容性

`CObject` 不支持多重继承。 派生类只能有一个 `CObject` 基类，并且该基类 `CObject` 必须在层次结构中最左边。 但允许 `CObject` 在右侧多继承分支中具有结构和非派生类。

`CObject`如果在类实现和声明中使用某些可选的宏，则可以从派生中获得重大益处。

第一级宏 [`DECLARE_DYNAMIC`](run-time-object-model-services.md#declare_dynamic) 和 [`IMPLEMENT_DYNAMIC`](run-time-object-model-services.md#implement_dynamic) 允许对类名称及其在层次结构中的位置的运行时访问。 这反过来又允许有意义的诊断转储。

第二级宏（ [`DECLARE_SERIAL`](run-time-object-model-services.md#declare_serial) 和 [`IMPLEMENT_SERIAL`](run-time-object-model-services.md#implement_serial) ）包含第一级宏的所有功能，并且使对象可以与 "存档" 进行 "序列化"。

有关一般和使用派生 Microsoft 基础类和 c + + 类的信息 `CObject` ，请参阅 [使用 CObject](../../mfc/using-cobject.md) 和 [序列化](../../mfc/serialization-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CObject`

## <a name="requirements"></a>要求

**标头：**`afx.h`

## <a name="cobjectassertvalid"></a><a name="assertvalid"></a> CObject：： AssertValid

验证此对象的完整性。

```cpp
virtual void AssertValid() const;
```

### <a name="remarks"></a>备注

`AssertValid` 通过检查此对象的内部状态来执行有效性检查。 在库的调试版本中， `AssertValid` 可以断言，然后终止程序，并在其中列出断言失败的行号和文件名。

编写您自己的类时，应重写该 `AssertValid` 函数，以便为您自己和您的类的其他用户提供诊断服务。 重写 `AssertValid` 通常在 `AssertValid` 检查派生类的唯一数据成员之前调用其基类的函数。

由于 `AssertValid` 是一个 **`const`** 函数，因此不允许在测试期间更改对象状态。 您自己的派生类 `AssertValid` 函数不应引发异常，而应断言它们是否检测到无效的对象数据。

"有效性" 的定义取决于对象的类。 作为一种规则，该函数应执行 "浅层检查"。 也就是说，如果对象包含指向其他对象的指针，它应检查指针是否不是 `NULL` ，但不应对指针所引用的对象执行有效性测试。

### <a name="example"></a>示例

[`CObList::CObList`](../../mfc/reference/coblist-class.md#coblist)有关 `CAge` 所有示例中使用的类的列表，请参阅 `CObject` 。

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

有关其他示例，请参阅 [`AfxDoForAllObjects`](diagnostic-services.md#afxdoforallobjects) 。

## <a name="cobjectcobject"></a><a name="cobject"></a> CObject：： CObject

这些函数是标准 `CObject` 构造函数。

```cpp
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>参数

*objectSrc*\
对另一个的引用 `CObject`

### <a name="remarks"></a>备注

默认版本自动由派生类的构造函数调用。

如果你的类可序列化 (它将 `IMPLEMENT_SERIAL` 宏合并) ，则你必须在类声明中 (具有不带) 参数的构造函数的默认构造函数。 如果不需要默认构造函数，请声明私有或受保护的 "empty" 构造函数。 有关详细信息，请[参阅 `CObject` 使用](../../mfc/using-cobject.md)。

标准 c + + 默认类复制构造函数执行成员成员复制。 `CObject`如果需要类的复制构造函数但不可用，则私有复制构造函数的存在可保证编译器错误消息。 如果类需要此功能，请提供复制构造函数。

### <a name="example"></a>示例

[`CObList::CObList`](../../mfc/reference/coblist-class.md#coblist)有关 `CAge` 示例中使用的类的列表，请参阅 `CObject` 。

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

## <a name="cobjectdump"></a><a name="dump"></a> CObject：:D ump

将对象的内容转储到 [`CDumpContext`](../../mfc/reference/cdumpcontext-class.md) 对象。

```cpp
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>参数

*台*\
用于转储的诊断转储上下文（通常为） `afxDump` 。

### <a name="remarks"></a>备注

编写您自己的类时，应重写该 `Dump` 函数，以便为您自己和您的类的其他用户提供诊断服务。 重写 `Dump` 通常在 `Dump` 输出派生类的唯一数据成员之前调用其基类的函数。 `CObject::Dump` 如果类使用或宏，则打印类 `IMPLEMENT_DYNAMIC` 名 `IMPLEMENT_SERIAL` 。

> [!NOTE]
> `Dump`函数不应在输出的末尾处打印换行符。

`Dump` 调用仅在 Microsoft 基础类库的调试版本中才有意义。 你应将调用、函数声明和函数实现用方括号括起来 `#ifdef _DEBUG` ， `#endif` 以便进行条件编译。

由于 `Dump` 是一个 **`const`** 函数，因此不允许在转储期间更改对象状态。

插入指针时， [ `CDumpContext` 插入 ( # A2) 运算符](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt)调用 `Dump` `CObject` 。

`Dump` 仅允许对象的 "非循环" 转储。 例如，你可以转储对象列表，但如果其中一个对象是列表本身，则最终会使堆栈溢出。

### <a name="example"></a>示例

[`CObList::CObList`](../../mfc/reference/coblist-class.md#coblist)有关 `CAge` 所有示例中使用的类的列表，请参阅 `CObject` 。

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

## <a name="cobjectgetruntimeclass"></a><a name="getruntimeclass"></a> CObject：： GetRuntimeClass

返回 `CRuntimeClass` 与此对象的类相对应的结构。

```cpp
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>返回值

指向与 [`CRuntimeClass`](../../mfc/reference/cruntimeclass-structure.md) 此对象的类相对应的结构的指针; 从不 **`NULL`** 。

### <a name="remarks"></a>备注

`CRuntimeClass`每个派生类都有一个结构 `CObject` 。 结构成员如下所示：

- **`LPCSTR m_lpszClassName`** 一个以 null 结尾的字符串，其中包含 ASCII 类名。
- **`int m_nObjectSize`** 对象的大小（以字节为单位）。 如果对象具有指向已分配内存的数据成员，则不包含该内存的大小。
- **`UINT m_wSchema`** 不可序列化类) 的架构编号 (-1。 [`IMPLEMENT_SERIAL`](run-time-object-model-services.md#implement_serial)有关架构号的说明，请参阅宏。

- **`CObject* (PASCAL* m_pfnCreateObject)()`** 指向创建类的对象的默认构造函数的函数指针 (仅当类支持动态创建时有效;否则，将返回 **`NULL`**) 。

- **`CRuntimeClass* (PASCAL* m_pfn_GetBaseClass )()`** 如果你的应用程序动态链接到 MFC 的 AFXDLL 版本，则为指向返回 `CRuntimeClass` 基类结构的函数的指针。

- **`CRuntimeClass* m_pBaseClass`** 如果应用程序静态链接到 MFC，则为指向基类的 `CRuntimeClass` 结构的指针。

此函数要求使用 [`IMPLEMENT_DYNAMIC`](run-time-object-model-services.md#implement_dynamic) [`IMPLEMENT_DYNCREATE`](run-time-object-model-services.md#implement_dyncreate) [`IMPLEMENT_SERIAL`](run-time-object-model-services.md#implement_serial) 类实现中的、或宏。 否则，会获得错误的结果。

### <a name="example"></a>示例

[`CObList::CObList`](../../mfc/reference/coblist-class.md#coblist)有关 `CAge` 所有示例中使用的类的列表，请参阅 `CObject` 。

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

## <a name="cobjectiskindof"></a><a name="iskindof"></a> CObject：： IsKindOf

测试与给定类的此对象的关系。

```cpp
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>参数

*`pClass`*\
指向 [`CRuntimeClass`](../../mfc/reference/cruntimeclass-structure.md) 与派生类关联的结构的指针 `CObject` 。

### <a name="return-value"></a>返回值

如果对象对应于类，则为非零;否则为0。

### <a name="remarks"></a>备注

此函数 *`pClass`* 将测试 (1) 它是指定类的对象还是 (2) 它是派生自指定类的类的对象。 此函数仅适用于使用 [`DECLARE_DYNAMIC`](run-time-object-model-services.md#declare_dynamic) 、 [`DECLARE_DYNCREATE`](run-time-object-model-services.md#declare_dyncreate) 或宏声明的类 [`DECLARE_SERIAL`](run-time-object-model-services.md#declare_serial) 。

不要广泛使用此函数，因为它违背 c + + 多态性功能。 改用虚函数。

### <a name="example"></a>示例

[`CObList::CObList`](../../mfc/reference/coblist-class.md#coblist)有关 `CAge` 所有示例中使用的类的列表，请参阅 `CObject` 。

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

## <a name="cobjectisserializable"></a><a name="isserializable"></a> CObject：： IsSerializable

测试此对象是否适用于序列化。

```cpp
BOOL IsSerializable() const;
```

### <a name="return-value"></a>返回值

如果此对象可以序列化，则为非零值;否则为0。

### <a name="remarks"></a>备注

要使类可序列化，它的声明必须包含 [`DECLARE_SERIAL`](run-time-object-model-services.md#declare_serial) 宏，且实现必须包含 [`IMPLEMENT_SERIAL`](run-time-object-model-services.md#implement_serial) 宏。

> [!NOTE]
> 不要覆盖此函数。

### <a name="example"></a>示例

[`CObList::CObList`](../../mfc/reference/coblist-class.md#coblist)有关 `CAge` 所有示例中使用的类的列表，请参阅 `CObject` 。

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

## <a name="cobjectoperator-delete"></a><a name="operator_delete"></a> CObject：： operator delete

对于库的发行版，运算符 **`delete`** 释放由运算符分配的内存 **`new`** 。

```cpp
void PASCAL operator delete(void* p);

void PASCAL operator delete(
    void* p,
    void* pPlace);

void PASCAL operator delete(
    void* p,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>备注

在调试版本中，运算符 **`delete`** 参与了用于检测内存泄漏的分配监视方案。

如果使用代码行

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

之前的任何实现。然后，将使用的第三个版本 **`delete`** ，将文件名和行号存储在已分配的块中供以后报告使用。 无需担心提供额外的参数;宏负责处理此操作。

即使不 `DEBUG_NEW` 在调试模式下使用，也仍会获得泄漏检测，但不需要上文所述的源文件行号报告。

如果重写运算符 **`new`** 和 **`delete`** ，则使此诊断功能。

### <a name="example"></a>示例

[`CObList::CObList`](../../mfc/reference/coblist-class.md#coblist)有关 `CAge` 示例中使用的类的列表，请参阅 `CObject` 。

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

## <a name="cobjectoperator-new"></a><a name="operator_new"></a> CObject：： operator new

对于库的发行版，操作员 **`new`** 会以类似于的方式执行最佳的内存分配 `malloc` 。

```cpp
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>备注

在调试版本中，运算符 **`new`** 参与了用于检测内存泄漏的分配监视方案。

如果使用代码行

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

之前的任何实现。然后，将使用的第二个版本 **`new`** ，将文件名和行号存储在已分配的块中供以后报告使用。 无需担心提供额外的参数;宏负责处理此操作。

即使不 `DEBUG_NEW` 在调试模式下使用，也仍会获得泄漏检测，但不需要上文所述的源文件行号报告。

> [!NOTE]
> 如果重写此运算符，则还必须重写 **`delete`** 。 不要使用标准库 `_new_handler` 函数。

### <a name="example"></a>示例

[`CObList::CObList`](../../mfc/reference/coblist-class.md#coblist)有关 `CAge` 示例中使用的类的列表，请参阅 `CObject` 。

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

## <a name="cobjectserialize"></a><a name="serialize"></a> CObject：：串行化

从存档读取该对象或将该对象写入存档。

```cpp
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>参数

*`ar`*\
要 `CArchive` 序列化到或的对象。

### <a name="remarks"></a>备注

重写要 `Serialize` 序列化的每个类。 重写 `Serialize` 必须先调用 `Serialize` 其基类的函数。

还必须 [`DECLARE_SERIAL`](run-time-object-model-services.md#declare_serial) 在类声明中使用宏，并且必须 [`IMPLEMENT_SERIAL`](run-time-object-model-services.md#implement_serial) 在实现中使用宏。

使用 [`CArchive::IsLoading`](../../mfc/reference/carchive-class.md#isloading) 或 [`CArchive::IsStoring`](../../mfc/reference/carchive-class.md#isstoring) 来确定存档是否正在加载或存储。

`Serialize` 由和调用 [`CArchive::ReadObject`](../../mfc/reference/carchive-class.md#readobject) [`CArchive::WriteObject`](../../mfc/reference/carchive-class.md#writeobject) 。 这些函数与 `CArchive` 插入运算符相关联 ( **`<<`**) 和 () 的提取运算符 **`>>`** 。

有关序列化示例，请参阅 [序列化对象一](../../mfc/serialization-serializing-an-object.md)文。

### <a name="example"></a>示例

[`CObList::CObList`](../../mfc/reference/coblist-class.md#coblist)有关 `CAge` 所有示例中使用的类的列表，请参阅 `CObject` 。

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)
