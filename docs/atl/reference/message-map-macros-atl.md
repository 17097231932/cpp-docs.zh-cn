---
title: " (ATL) 的消息映射宏"
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::ALT_MSG_MAP
- atlwin/ATL::BEGIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_ALT
- atlwin/ATL::CHAIN_MSG_MAP_ALT_MEMBER
- atlwin/ATL::CHAIN_MSG_MAP
- atlwin/ATL::CHAIN_MSG_MAP_DYNAMIC
- atlwin/ATL::CHAIN_MSG_MAP_MEMBER
- atlwin/ATL::COMMAND_CODE_HANDLER
- atlwin/ATL::COMMAND_HANDLER
- atlwin/ATL::COMMAND_ID_HANDLER
- atlwin/ATL::COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::COMMAND_RANGE_HANDLER
- atlwin/ATL::DECLARE_EMPTY_MSG_MAP
- atlwin/ATL::DEFAULT_REFLECTION_HANDLER
- atlwin/ATL::END_MSG_MAP
- atlwin/ATL::FORWARD_NOTIFICATIONS
- atlwin/ATL::MESSAGE_HANDLER
- atlwin/ATL::MESSAGE_RANGE_HANDLER
- atlwin/ATL::NOTIFY_CODE_HANDLER
- atlwin/ATL::NOTIFY_HANDLER
- atlwin/ATL::NOTIFY_ID_HANDLER
- atlwin/ATL::NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::NOTIFY_RANGE_HANDLER
- atlwin/ATL::REFLECT_NOTIFICATIONS
- atlwin/ATL::REFLECTED_COMMAND_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_ID_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_COMMAND_RANGE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_ID_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_CODE_HANDLER
- atlwin/ATL::REFLECTED_NOTIFY_RANGE_HANDLER
ms.assetid: eefdd546-8934-4a30-b263-9c06a8addcbd
ms.openlocfilehash: 9917f31dbb115552cf9dc9bde24f7b6921611750
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835293"
---
# <a name="message-map-macros-atl"></a> (ATL) 的消息映射宏

这些宏定义消息映射和条目。

|名称|说明|
|-|-|
|[ALT_MSG_MAP](#alt_msg_map)|标记备用消息映射的开头。|
|[BEGIN_MSG_MAP](#begin_msg_map)|标记默认消息映射的开头。|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|链接到基类中的备用消息映射。|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|链接到类的数据成员中的备用消息映射。|
|[CHAIN_MSG_MAP](#chain_msg_map)|链接到基类中的默认消息映射。|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|在运行时链接到其他类中的消息映射。|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|链接到类的数据成员中的默认消息映射。|
|[COMMAND_CODE_HANDLER](#command_code_handler)|根据通知代码，将 WM_COMMAND 消息映射到处理程序函数。|
|[COMMAND_HANDLER](#command_handler)|根据通知代码以及菜单项、控件或快捷键的标识符，将 WM_COMMAND 消息映射到处理程序函数。|
|[COMMAND_ID_HANDLER](#command_id_handler)|根据菜单项、控件或快捷键的标识符，将 WM_COMMAND 消息映射到处理程序函数。|
|[COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)|根据通知代码和连续范围的控件标识符，将 WM_COMMAND 消息映射到处理程序函数。|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|基于一系列连续的控件标识符，将 WM_COMMAND 消息映射到处理程序函数。|
|[DECLARE_EMPTY_MSG_MAP](#declare_empty_msg_map)|实现空消息映射。|
|[DEFAULT_REFLECTION_HANDLER](#default_reflection_handler)|为尚未处理的反射消息提供默认处理程序。|
|[END_MSG_MAP](#end_msg_map)|标记消息映射的结尾。|
|[FORWARD_NOTIFICATIONS](#forward_notifications)|将通知消息转发到父窗口。|
|[MESSAGE_HANDLER](#message_handler)|将 Windows 消息映射到处理程序函数。|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|将一系列连续的 Windows 消息映射到处理程序函数。|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|根据通知代码，将 WM_NOTIFY 消息映射到处理程序函数。|
|[NOTIFY_HANDLER](#notify_handler)|根据通知代码和控件标识符，将 WM_NOTIFY 消息映射到处理程序函数。|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|根据控件标识符，将 WM_NOTIFY 消息映射到处理程序函数。|
|[NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)|根据通知代码和连续范围的控件标识符，将 WM_NOTIFY 消息映射到处理程序函数。|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|基于一系列连续的控件标识符，将 WM_NOTIFY 消息映射到处理程序函数。|
|[REFLECT_NOTIFICATIONS](#reflect_notifications)|将通知消息反映回发送它们的窗口。|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|根据通知代码，将反射的 WM_COMMAND 消息映射到处理程序函数。|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|根据通知代码以及菜单项、控件或快捷键的标识符，将反射的 WM_COMMAND 消息映射到处理程序函数。|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|基于菜单项、控件或快捷键的标识符，将反射的 WM_COMMAND 消息映射到处理程序函数。|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|根据通知代码和连续范围的控件标识符，将反射的 WM_COMMAND 消息映射到处理程序函数。|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|基于一系列连续的控件标识符，将反射的 WM_COMMAND 消息映射到处理程序函数。|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|根据通知代码，将反射的 WM_NOTIFY 消息映射到处理程序函数。|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|根据通知代码和控件标识符，将反射的 WM_NOTIFY 消息映射到处理程序函数。|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|基于控件标识符，将反射的 WM_NOTIFY 消息映射到处理程序函数。|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|根据通知代码和连续范围的控件标识符，将反射的 WM_NOTIFY 消息映射到处理程序函数。|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|基于一系列连续的控件标识符，将反射的 WM_NOTIFY 消息映射到处理程序函数。|

## <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="alt_msg_map"></a><a name="alt_msg_map"></a> ALT_MSG_MAP

标记备用消息映射的开头。

```
ALT_MSG_MAP(msgMapID)
```

### <a name="parameters"></a>参数

*msgMapID*<br/>
中消息映射标识符。

### <a name="remarks"></a>注解

ATL 按数字标识每个消息。 默认消息映射 (使用 BEGIN_MSG_MAP 宏) 标识，由0标识。 替换消息映射由 *msgMapID*标识。

消息映射用于处理发送到窗口的消息。 例如，使用 [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) 可以指定包含对象中的消息映射的标识符。 [CContainedWindow：： WindowProc](ccontainedwindowt-class.md#windowproc) 然后使用此消息映射将包含窗口的消息定向到适当的处理程序函数或另一个消息映射。 有关声明处理函数的宏列表，请参阅 [BEGIN_MSG_MAP](#begin_msg_map)。

始终使用 BEGIN_MSG_MAP 开始消息映射。 然后，可以声明后续替换消息映射。

[END_MSG_MAP](#end_msg_map)宏标记消息映射的结尾。 请注意，始终只有一个 BEGIN_MSG_MAP 和 END_MSG_MAP 的实例。

有关使用 ATL 中的消息映射的详细信息，请参阅 [消息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>示例

下面的示例演示默认消息映射和一个备用消息映射，每个消息映射包含一个处理程序函数：

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

下一个示例显示了两个替代消息映射。 默认消息映射为空。

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="begin_msg_map"></a><a name="begin_msg_map"></a> BEGIN_MSG_MAP

标记默认消息映射的开头。

```
BEGIN_MSG_MAP(theClass)
```

### <a name="parameters"></a>参数

*类*<br/>
中包含消息映射的类的名称。

### <a name="remarks"></a>注解

[CWindowImpl：： WindowProc](cwindowimpl-class.md#windowproc) 使用默认消息映射处理发送到窗口的消息。 消息映射将消息定向到适当的处理程序函数或其他消息映射。

以下宏将消息映射到处理程序函数。 此函数必须在 *类*中定义。

|宏|描述|
|-----------|-----------------|
|[MESSAGE_HANDLER](#message_handler)|将 Windows 消息映射到处理程序函数。|
|[MESSAGE_RANGE_HANDLER](#message_range_handler)|将一系列连续的 Windows 消息映射到处理程序函数。|
|[COMMAND_HANDLER](#command_handler)|根据通知代码以及菜单项、控件或快捷键的标识符，将 WM_COMMAND 消息映射到处理程序函数。|
|[COMMAND_ID_HANDLER](#command_id_handler)|根据菜单项、控件或快捷键的标识符，将 WM_COMMAND 消息映射到处理程序函数。|
|[COMMAND_CODE_HANDLER](#command_handler)|根据通知代码，将 WM_COMMAND 消息映射到处理程序函数。|
|[COMMAND_RANGE_HANDLER](#command_range_handler)|基于菜单项、控件或快捷键的标识符，将连续的 WM_COMMAND 消息范围映射到处理程序函数。|
|[NOTIFY_HANDLER](#notify_handler)|根据通知代码和控件标识符，将 WM_NOTIFY 消息映射到处理程序函数。|
|[NOTIFY_ID_HANDLER](#notify_id_handler)|根据控件标识符，将 WM_NOTIFY 消息映射到处理程序函数。|
|[NOTIFY_CODE_HANDLER](#notify_code_handler)|根据通知代码，将 WM_NOTIFY 消息映射到处理程序函数。|
|[NOTIFY_RANGE_HANDLER](#notify_range_handler)|基于控件标识符，将连续的 WM_NOTIFY 消息范围映射到处理程序函数。|

以下宏将消息定向到另一消息映射。 此过程称为 "链接"。

|宏|描述|
|-----------|-----------------|
|[CHAIN_MSG_MAP](#chain_msg_map)|链接到基类中的默认消息映射。|
|[CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)|链接到类的数据成员中的默认消息映射。|
|[CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)|链接到基类中的备用消息映射。|
|[CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)|链接到类的数据成员中的备用消息映射。|
|[CHAIN_MSG_MAP_DYNAMIC](#chain_msg_map_dynamic)|在运行时链接到其他类中的默认消息映射。|

以下宏直接从父窗口 "反射" 消息。 例如，控件通常将通知消息发送到其父窗口进行处理，但父窗口可以将消息反映回控件。

|宏|描述|
|-----------|-----------------|
|[REFLECTED_COMMAND_HANDLER](#reflected_command_handler)|根据通知代码以及菜单项、控件或快捷键的标识符，将反射的 WM_COMMAND 消息映射到处理程序函数。|
|[REFLECTED_COMMAND_ID_HANDLER](#reflected_command_id_handler)|基于菜单项、控件或快捷键的标识符，将反射的 WM_COMMAND 消息映射到处理程序函数。|
|[REFLECTED_COMMAND_CODE_HANDLER](#reflected_command_code_handler)|根据通知代码，将反射的 WM_COMMAND 消息映射到处理程序函数。|
|[REFLECTED_COMMAND_RANGE_HANDLER](#reflected_command_range_handler)|基于一系列连续的控件标识符，将反射的 WM_COMMAND 消息映射到处理程序函数。|
|[REFLECTED_COMMAND_RANGE_CODE_HANDLER](#reflected_command_range_code_handler)|根据通知代码和连续范围的控件标识符，将反射的 WM_COMMAND 消息映射到处理程序函数。|
|[REFLECTED_NOTIFY_HANDLER](#reflected_notify_handler)|根据通知代码和控件标识符，将反射的 WM_NOTIFY 消息映射到处理程序函数。|
|[REFLECTED_NOTIFY_ID_HANDLER](#reflected_notify_id_handler)|基于控件标识符，将反射的 WM_NOTIFY 消息映射到处理程序函数。|
|[REFLECTED_NOTIFY_CODE_HANDLER](#reflected_notify_code_handler)|根据通知代码，将反射的 WM_NOTIFY 消息映射到处理程序函数。|
|[REFLECTED_NOTIFY_RANGE_HANDLER](#reflected_notify_range_handler)|基于一系列连续的控件标识符，将反射的 WM_NOTIFY 消息映射到处理程序函数。|
|[REFLECTED_NOTIFY_RANGE_CODE_HANDLER](#reflected_notify_range_code_handler)|根据通知代码和连续范围的控件标识符，将反射的 WM_NOTIFY 消息映射到处理程序函数。|

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#102](../../atl/codesnippet/cpp/message-map-macros-atl_3.h)]

当 `CMyExtWindow` 对象收到 WM_PAINT 消息时，会将该消息定向到 `CMyExtWindow::OnPaint` 进行实际处理。 如果 `OnPaint` 指示消息需要进一步处理，则该消息将被定向到中的默认消息映射 `CMyBaseWindow` 。

除了默认消息映射外，还可以使用 [ALT_MSG_MAP](#alt_msg_map)定义备用消息映射。 始终使用 BEGIN_MSG_MAP 开始消息映射。 然后，可以声明后续替换消息映射。 下面的示例演示默认消息映射和一个备用消息映射，每个消息映射包含一个处理程序函数：

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

下一个示例显示了两个替代消息映射。 默认消息映射为空。

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

[END_MSG_MAP](#end_msg_map)宏标记消息映射的结尾。 请注意，始终只有一个 BEGIN_MSG_MAP 和 END_MSG_MAP 的实例。

有关使用 ATL 中的消息映射的详细信息，请参阅 [消息映射](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="chain_msg_map_alt"></a><a name="chain_msg_map_alt"></a> CHAIN_MSG_MAP_ALT

定义消息映射中的条目。

```
CHAIN_MSG_MAP_ALT(theChainClass, msgMapID)
```

### <a name="parameters"></a>参数

*theChainClass*<br/>
中包含消息映射的基类的名称。

*msgMapID*<br/>
中消息映射标识符。

### <a name="remarks"></a>注解

CHAIN_MSG_MAP_ALT 将消息定向到基类中的备用消息映射。 必须已使用 [ALT_MSG_MAP (msgMapID) ](#alt_msg_map)声明了此替换消息映射。 若要将消息定向到基类的默认消息映射 (使用 [BEGIN_MSG_MAP](#begin_msg_map)) 进行声明，请使用 CHAIN_MSG_MAP。 有关示例，请参阅 [CHAIN_MSG_MAP](#chain_msg_map)。

> [!NOTE]
> 始终使用 BEGIN_MSG_MAP 开始消息映射。 然后，可以声明后续替换消息映射 ALT_MSG_MAP。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的结尾。 每个消息映射必须恰好具有一个 BEGIN_MSG_MAP 实例和 END_MSG_MAP。

有关使用 ATL 中的消息映射的详细信息，请参阅 [消息映射](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="chain_msg_map_alt_member"></a><a name="chain_msg_map_alt_member"></a> CHAIN_MSG_MAP_ALT_MEMBER

定义消息映射中的条目。

```
CHAIN_MSG_MAP_ALT_MEMBER(theChainMember, msgMapID)
```

### <a name="parameters"></a>参数

*theChainMember*<br/>
中包含消息映射的数据成员的名称。

*msgMapID*<br/>
中消息映射标识符。

### <a name="remarks"></a>注解

CHAIN_MSG_MAP_ALT_MEMBER 将消息定向到数据成员中的备用消息映射。 必须已使用 [ALT_MSG_MAP (msgMapID) ](#alt_msg_map)声明了此替换消息映射。 若要将消息定向到数据成员的默认消息映射 (使用 [BEGIN_MSG_MAP](#begin_msg_map)) 进行声明，请使用 CHAIN_MSG_MAP_MEMBER。 有关示例，请参阅 [CHAIN_MSG_MAP_MEMBER](#chain_msg_map_member)。

> [!NOTE]
> 始终使用 BEGIN_MSG_MAP 开始消息映射。 然后，可以声明后续替换消息映射 ALT_MSG_MAP。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的结尾。 每个消息映射必须恰好具有一个 BEGIN_MSG_MAP 实例和 END_MSG_MAP。

有关使用 ATL 中的消息映射的详细信息，请参阅 [消息映射](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="chain_msg_map"></a><a name="chain_msg_map"></a> CHAIN_MSG_MAP

定义消息映射中的条目。

```
CHAIN_MSG_MAP(theChainClass)
```

### <a name="parameters"></a>参数

*theChainClass*<br/>
中包含消息映射的基类的名称。

### <a name="remarks"></a>注解

CHAIN_MSG_MAP 将消息定向到 (使用 [BEGIN_MSG_MAP](#begin_msg_map)) 声明的基类默认消息映射。 若要将消息定向到基类的替代消息映射 (使用 [ALT_MSG_MAP](#alt_msg_map)) 进行声明，请使用 [CHAIN_MSG_MAP_ALT](#chain_msg_map_alt)。

> [!NOTE]
> 始终使用 BEGIN_MSG_MAP 开始消息映射。 然后，可以声明后续替换消息映射 ALT_MSG_MAP。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的结尾。 每个消息映射必须恰好具有一个 BEGIN_MSG_MAP 实例和 END_MSG_MAP。

有关使用 ATL 中的消息映射的详细信息，请参阅 [消息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#107](../../atl/codesnippet/cpp/message-map-macros-atl_4.h)]

此示例演示了以下内容：

- 如果某个窗口过程使用 `CMyClass` 的是默认消息映射，并且 `OnPaint` 未处理消息，则该消息将被定向到 `CMyBaseClass` 默认消息映射进行处理。

- 如果某个窗口过程在中使用第一个备用消息映射 `CMyClass` ，则所有消息都将定向到 `CMyBaseClass` 默认消息映射。

- 如果某个窗口过程正在使用 `CMyClass` 第二个替代消息映射，并且 `OnChar` 未处理消息，则会将该消息定向到中的指定替换消息映射 `CMyBaseClass` 。 `CMyBaseClass` 必须声明此消息映射与 ALT_MSG_MAP (1) 。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="chain_msg_map_dynamic"></a><a name="chain_msg_map_dynamic"></a> CHAIN_MSG_MAP_DYNAMIC

定义消息映射中的条目。

```
CHAIN_MSG_MAP_DYNAMIC(dynaChainID)
```

### <a name="parameters"></a>参数

*dynaChainID*<br/>
中对象的消息映射的唯一标识符。

### <a name="remarks"></a>注解

CHAIN_MSG_MAP_DYNAMIC 将运行时的消息定向到另一个对象中的默认消息映射。 对象及其消息映射与通过[CDynamicChain：： SetChainEntry](cdynamicchain-class.md#setchainentry)定义的*dynaChainID*相关联。 必须从派生类，才能 `CDynamicChain` 使用 CHAIN_MSG_MAP_DYNAMIC。 有关示例，请参阅 [CDynamicChain](../../atl/reference/cdynamicchain-class.md) 概述。

> [!NOTE]
> 始终使用 [BEGIN_MSG_MAP](#begin_msg_map)开始消息映射。 然后，可以声明后续替换消息映射 ALT_MSG_MAP。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的结尾。 每个消息映射必须恰好具有一个 BEGIN_MSG_MAP 实例和 END_MSG_MAP。

有关使用 ATL 中的消息映射的详细信息，请参阅 [消息映射](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="chain_msg_map_member"></a><a name="chain_msg_map_member"></a> CHAIN_MSG_MAP_MEMBER

定义消息映射中的条目。

```
CHAIN_MSG_MAP_MEMBER(theChainMember)
```

### <a name="parameters"></a>参数

*theChainMember*<br/>
中包含消息映射的数据成员的名称。

### <a name="remarks"></a>注解

CHAIN_MSG_MAP_MEMBER 将消息定向到 (使用 [BEGIN_MSG_MAP](#begin_msg_map)) 声明的数据成员默认消息映射。 若要将消息定向到数据成员的备用消息映射 (使用 [ALT_MSG_MAP](#alt_msg_map)) 进行声明，请使用 [CHAIN_MSG_MAP_ALT_MEMBER](#chain_msg_map_alt_member)。

> [!NOTE]
> 始终使用 BEGIN_MSG_MAP 开始消息映射。 然后，可以声明后续替换消息映射 ALT_MSG_MAP。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的结尾。 每个消息映射必须恰好具有一个 BEGIN_MSG_MAP 实例和 END_MSG_MAP。

有关使用 ATL 中的消息映射的详细信息，请参阅 [消息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#108](../../atl/codesnippet/cpp/message-map-macros-atl_5.h)]

此示例演示了以下内容：

- 如果某个窗口过程使用 `CMyClass` 的是默认消息映射，并且 `OnPaint` 未处理消息，则该消息将被定向到 `m_obj` 默认消息映射进行处理。

- 如果某个窗口过程在中使用第一个备用消息映射 `CMyClass` ，则所有消息都将定向到 `m_obj` 默认消息映射。

- 如果某个窗口过程正在使用 `CMyClass` 第二个替代消息映射，并且 `OnChar` 未处理消息，则会将该消息定向到的指定替换消息映射 `m_obj` 。 类 `CMyContainedClass` 必须已使用 (1) ALT_MSG_MAP 声明此消息映射。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="command_code_handler"></a><a name="command_code_handler"></a> COMMAND_CODE_HANDLER

与 [COMMAND_HANDLER](#command_handler)类似，但仅基于通知代码映射 [WM_COMMAND](/windows/win32/menurc/wm-command) 消息。

```
COMMAND_CODE_HANDLER(code, func)
```

### <a name="parameters"></a>参数

*code*<br/>
中通知代码。

*func*<br/>
中消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="command_handler"></a><a name="command_handler"></a> COMMAND_HANDLER

定义消息映射中的条目。

```
COMMAND_HANDLER(id, code, func)
```

### <a name="parameters"></a>参数

*id*<br/>
中菜单项、控件或快捷键的标识符。

*code*<br/>
中通知代码。

*func*<br/>
中消息处理程序函数的名称。

### <a name="remarks"></a>注解

COMMAND_HANDLER 根据通知代码和控件标识符，将 [WM_COMMAND](/windows/win32/menurc/wm-command) 消息映射到指定的处理程序函数。 例如：

[!code-cpp[NVC_ATL_Windowing#119](../../atl/codesnippet/cpp/message-map-macros-atl_6.h)]

必须按如下所示定义 COMMAND_HANDLER 宏中指定的任何函数：

`LRESULT CommandHandler(WORD wNotifyCode, WORD wID, HWND hWndCtl, BOOL& bHandled);`

在调用之前，消息映射将设置 `bHandled` 为 TRUE `CommandHandler` 。 如果 `CommandHandler` 未完全处理消息，则应将其设置 `bHandled` 为 FALSE，以指示消息需要进一步处理。

> [!NOTE]
> 始终使用 [BEGIN_MSG_MAP](#begin_msg_map)开始消息映射。 然后，可以声明后续替换消息映射 [ALT_MSG_MAP](#alt_msg_map)。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的结尾。 每个消息映射必须恰好具有一个 BEGIN_MSG_MAP 实例和 END_MSG_MAP。

除了 COMMAND_HANDLER 之外，还可以使用 [MESSAGE_HANDLER](#message_handler) 在不考虑标识符或代码的情况下映射 WM_COMMAND 消息。 在这种情况下， `MESSAGE_HANDLER(WM_COMMAND, OnHandlerFunction)` 会将所有 WM_COMMAND 消息定向到 `OnHandlerFunction` 。

有关使用 ATL 中的消息映射的详细信息，请参阅 [消息映射](../../atl/message-maps-atl.md)。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="command_id_handler"></a><a name="command_id_handler"></a> COMMAND_ID_HANDLER

与 [COMMAND_HANDLER](#command_handler)类似，但仅基于菜单项、控件或快捷键的标识符映射 [WM_COMMAND](/windows/win32/menurc/wm-command) 消息。

```
COMMAND_ID_HANDLER(id, func)
```

### <a name="parameters"></a>参数

*id*<br/>
中发送消息的菜单项、控件或快捷键的标识符。

*func*<br/>
中消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="command_range_code_handler"></a><a name="command_range_code_handler"></a> COMMAND_RANGE_CODE_HANDLER

与 [COMMAND_RANGE_HANDLER](#command_range_handler)类似，但会将具有特定通知代码的消息从一系列控件 [WM_COMMAND](/windows/win32/menurc/wm-command) 映射到单个处理程序函数。

```
COMMAND_RANGE_CODE_HANDLER(idFirst, idLast, code, func)
```

### <a name="parameters"></a>参数

*idFirst*<br/>
中标记连续的控件标识符范围的开头。

*idLast*<br/>
中标记连续的控件标识符范围的结尾。

*code*<br/>
中通知代码。

*func*<br/>
中消息处理程序函数的名称。

### <a name="remarks"></a>注解

此范围基于发送消息的菜单项、控件或快捷键的标识符。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="command_range_handler"></a><a name="command_range_handler"></a> COMMAND_RANGE_HANDLER

与 [COMMAND_HANDLER](#command_handler)类似，但会将从一系列控件 [WM_COMMAND](/windows/win32/menurc/wm-command) 消息映射到单个处理程序函数。

```
COMMAND_RANGE_HANDLER( idFirst, idLast, func)
```

### <a name="parameters"></a>参数

*idFirst*<br/>
中标记连续的控件标识符范围的开头。

*idLast*<br/>
中标记连续的控件标识符范围的结尾。

*func*<br/>
中消息处理程序函数的名称。

### <a name="remarks"></a>注解

此范围基于发送消息的菜单项、控件或快捷键的标识符。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="declare_empty_msg_map"></a><a name="declare_empty_msg_map"></a> DECLARE_EMPTY_MSG_MAP

声明空消息映射。

```
DECLARE_EMPTY_MSG_MAP()
```

### <a name="remarks"></a>注解

DECLARE_EMPTY_MSG_MAP 是一种方便的宏，它调用宏 [BEGIN_MSG_MAP](#begin_msg_map) 并 [END_MSG_MAP](#end_msg_map) 创建空消息映射：

[!code-cpp[NVC_ATL_Windowing#122](../../atl/codesnippet/cpp/message-map-macros-atl_7.h)]

## <a name="default_reflection_handler"></a><a name="default_reflection_handler"></a> DEFAULT_REFLECTION_HANDLER

为将接收反射消息的子窗口 (控件) 提供默认处理程序;处理程序将向传递未处理的消息 `DefWindowProc` 。

```
DEFAULT_REFLECTION_HANDLER()
```

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="end_msg_map"></a><a name="end_msg_map"></a> END_MSG_MAP

标记消息映射的结尾。

```
END_MSG_MAP()
```

### <a name="remarks"></a>注解

始终使用 [BEGIN_MSG_MAP](#begin_msg_map) 宏来标记消息映射的开头。 使用 [ALT_MSG_MAP](#alt_msg_map) 声明后续替换消息映射。

请注意，始终只有一个 BEGIN_MSG_MAP 和 END_MSG_MAP 的实例。

有关使用 ATL 中的消息映射的详细信息，请参阅 [消息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>示例

下面的示例演示默认消息映射和一个备用消息映射，每个消息映射包含一个处理程序函数：

[!code-cpp[NVC_ATL_Windowing#98](../../atl/codesnippet/cpp/message-map-macros-atl_1.h)]

下一个示例显示了两个替代消息映射。 默认消息映射为空。

[!code-cpp[NVC_ATL_Windowing#99](../../atl/codesnippet/cpp/message-map-macros-atl_2.h)]

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="forward_notifications"></a><a name="forward_notifications"></a> FORWARD_NOTIFICATIONS

将通知消息转发到父窗口。

```
FORWARD_NOTIFICATIONS()
```

### <a name="remarks"></a>注解

将此宏指定为消息映射的一部分。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="message_handler"></a><a name="message_handler"></a> MESSAGE_HANDLER

定义消息映射中的条目。

```
MESSAGE_HANDLER( msg, func )
```

### <a name="parameters"></a>参数

*msg*<br/>
中Windows 消息。

*func*<br/>
中消息处理程序函数的名称。

### <a name="remarks"></a>注解

MESSAGE_HANDLER 将 Windows 消息映射到指定的处理程序函数。

必须按如下所示定义 MESSAGE_HANDLER 宏中指定的任何函数：

`LRESULT MessageHandler(UINT uMsg, WPARAM wParam, LPARAM lParam, BOOL& bHandled);`

在调用之前，消息映射将设置 `bHandled` 为 TRUE `MessageHandler` 。 如果 `MessageHandler` 未完全处理消息，则应将其设置 `bHandled` 为 FALSE，以指示消息需要进一步处理。

> [!NOTE]
> 始终使用 [BEGIN_MSG_MAP](#begin_msg_map)开始消息映射。 然后，可以声明后续替换消息映射 [ALT_MSG_MAP](#alt_msg_map)。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的结尾。 每个消息映射必须恰好具有一个 BEGIN_MSG_MAP 实例和 END_MSG_MAP。

除了 MESSAGE_HANDLER 之外，还可以使用 [COMMAND_HANDLER](#command_handler) 和 [NOTIFY_HANDLER](#notify_handler) 分别映射 [WM_COMMAND](/windows/win32/menurc/wm-command) 和 [WM_NOTIFY](/windows/win32/controls/wm-notify) 消息。

有关使用 ATL 中的消息映射的详细信息，请参阅 [消息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#129](../../atl/codesnippet/cpp/message-map-macros-atl_8.h)]

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="message_range_handler"></a><a name="message_range_handler"></a> MESSAGE_RANGE_HANDLER

与 [MESSAGE_HANDLER](#message_handler)类似，但将一系列 Windows 消息映射到单个处理程序函数。

```
MESSAGE_RANGE_HANDLER( msgFirst, msgLast, func )
```

### <a name="parameters"></a>参数

*msgFirst*<br/>
中标记连续消息范围的开头。

*msgLast*<br/>
中标记连续消息范围的结尾。

*func*<br/>
中消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="notify_code_handler"></a><a name="notify_code_handler"></a> NOTIFY_CODE_HANDLER

与 [NOTIFY_HANDLER](#notify_handler)类似，但仅基于通知代码映射 [WM_NOTIFY](/windows/win32/controls/wm-notify) 消息。

```
NOTIFY_CODE_HANDLER(cd, func)
```

### <a name="parameters"></a>参数

*cd*<br/>
中通知代码。

*func*<br/>
中消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="notify_handler"></a><a name="notify_handler"></a> NOTIFY_HANDLER

定义消息映射中的条目。

```
NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>参数

*id*<br/>
中发送消息的控件的标识符。

*cd*<br/>
中通知代码。

*func*<br/>
中消息处理程序函数的名称。

### <a name="remarks"></a>注解

NOTIFY_HANDLER 根据通知代码和控件标识符，将 [WM_NOTIFY](/windows/win32/controls/wm-notify) 消息映射到指定的处理程序函数。

必须按如下所示定义 NOTIFY_HANDLER 宏中指定的任何函数：

`LRESULT NotifyHandler(int idCtrl, LPNMHDR pnmh, BOOL& bHandled);`

在调用之前，消息映射将设置 `bHandled` 为 TRUE `NotifyHandler` 。 如果 `NotifyHandler` 未完全处理消息，则应将其设置 `bHandled` 为 FALSE，以指示消息需要进一步处理。

> [!NOTE]
> 始终使用 [BEGIN_MSG_MAP](#begin_msg_map)开始消息映射。 然后，可以声明后续替换消息映射 [ALT_MSG_MAP](#alt_msg_map)。 [END_MSG_MAP](#end_msg_map)宏标记消息映射的结尾。 每个消息映射必须恰好具有一个 BEGIN_MSG_MAP 实例和 END_MSG_MAP。

除了 NOTIFY_HANDLER 之外，还可以使用 [MESSAGE_HANDLER](#message_handler) 在不考虑标识符或代码的情况下映射 WM_NOTIFY 消息。 在这种情况下， `MESSAGE_HANDLER(WM_NOTIFY, OnHandlerFunction)` 会将所有 WM_NOTIFY 消息定向到 `OnHandlerFunction` 。

有关使用 ATL 中的消息映射的详细信息，请参阅 [消息映射](../../atl/message-maps-atl.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#130](../../atl/codesnippet/cpp/message-map-macros-atl_9.h)]

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="notify_id_handler"></a><a name="notify_id_handler"></a> NOTIFY_ID_HANDLER

与 [NOTIFY_HANDLER](#notify_handler)类似，但仅基于控件标识符映射 [WM_NOTIFY](/windows/win32/controls/wm-notify) 消息。

```
NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>参数

*id*<br/>
中发送消息的控件的标识符。

*func*<br/>
中消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="notify_range_code_handler"></a><a name="notify_range_code_handler"></a> NOTIFY_RANGE_CODE_HANDLER

与 [NOTIFY_RANGE_HANDLER](#notify_range_handler)类似，但会将具有特定通知代码的消息从一系列控件 [WM_NOTIFY](/windows/win32/controls/wm-notify) 映射到单个处理程序函数。

```
NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>参数

*idFirst*<br/>
中标记连续的控件标识符范围的开头。

*idLast*<br/>
中标记连续的控件标识符范围的结尾。

*cd*<br/>
中通知代码。

*func*<br/>
中消息处理程序函数的名称。

### <a name="remarks"></a>注解

此范围基于发送消息的控件的标识符。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="notify_range_handler"></a><a name="notify_range_handler"></a> NOTIFY_RANGE_HANDLER

与 [NOTIFY_HANDLER](#notify_handler)类似，但会将从一系列控件 [WM_NOTIFY](/windows/win32/controls/wm-notify) 消息映射到单个处理程序函数。

```
NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>参数

*idFirst*<br/>
中标记连续的控件标识符范围的开头。

*idLast*<br/>
中标记连续的控件标识符范围的结尾。

*func*<br/>
中消息处理程序函数的名称。

### <a name="remarks"></a>注解

此范围基于发送消息的控件的标识符。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="reflect_notifications"></a><a name="reflect_notifications"></a> REFLECT_NOTIFICATIONS

将通知消息反映回发送到子窗口 (控件) 。

```
REFLECT_NOTIFICATIONS()
```

### <a name="remarks"></a>注解

将此宏指定为父窗口的消息映射的一部分。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="reflected_command_code_handler"></a><a name="reflected_command_code_handler"></a> REFLECTED_COMMAND_CODE_HANDLER

与 [COMMAND_CODE_HANDLER](#command_code_handler)类似，但映射从父窗口反射的命令。

```
REFLECTED_COMMAND_CODE_HANDLER( code, func )
```

### <a name="parameters"></a>参数

*code*<br/>
中通知代码。

*func*<br/>
中消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="reflected_command_handler"></a><a name="reflected_command_handler"></a> REFLECTED_COMMAND_HANDLER

与 [COMMAND_HANDLER](#command_handler)类似，但映射从父窗口反射的命令。

```
REFLECTED_COMMAND_HANDLER( id, code, func )
```

### <a name="parameters"></a>参数

*id*<br/>
中菜单项、控件或快捷键的标识符。

*code*<br/>
中通知代码。

*func*<br/>
中消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="reflected_command_id_handler"></a><a name="reflected_command_id_handler"></a> REFLECTED_COMMAND_ID_HANDLER

与 [COMMAND_ID_HANDLER](#command_id_handler)类似，但映射从父窗口反射的命令。

```
REFLECTED_COMMAND_ID_HANDLER( id, func )
```

### <a name="parameters"></a>参数

*id*<br/>
中菜单项、控件或快捷键的标识符。

*func*<br/>
中消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="reflected_command_range_code_handler"></a><a name="reflected_command_range_code_handler"></a> REFLECTED_COMMAND_RANGE_CODE_HANDLER

与 [COMMAND_RANGE_CODE_HANDLER](#command_range_code_handler)类似，但映射从父窗口反射的命令。

```
REFLECTED_COMMAND_RANGE_CODE_HANDLER( idFirst, idLast, code, func )
```

### <a name="parameters"></a>参数

*idFirst*<br/>
中标记连续的控件标识符范围的开头。

*idLast*<br/>
中标记连续的控件标识符范围的结尾。

*code*<br/>
中通知代码。

*func*<br/>
中消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="reflected_command_range_handler"></a><a name="reflected_command_range_handler"></a> REFLECTED_COMMAND_RANGE_HANDLER

与 [COMMAND_RANGE_HANDLER](#command_range_handler)类似，但映射从父窗口反射的命令。

```
REFLECTED_COMMAND_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>参数

*idFirst*<br/>
中标记连续的控件标识符范围的开头。

*idLast*<br/>
中标记连续的控件标识符范围的结尾。

*func*<br/>
中消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="reflected_notify_code_handler"></a><a name="reflected_notify_code_handler"></a> REFLECTED_NOTIFY_CODE_HANDLER

与 [NOTIFY_CODE_HANDLER](#notify_code_handler)类似，但会映射从父窗口反射的通知。

```
REFLECTED_NOTIFY_CODE_HANDLER_EX( cd, func )
```

### <a name="parameters"></a>参数

*cd*<br/>
中通知代码。

*func*<br/>
中消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="reflected_notify_handler"></a><a name="reflected_notify_handler"></a> REFLECTED_NOTIFY_HANDLER

与 [NOTIFY_HANDLER](#notify_handler)类似，但会映射从父窗口反射的通知。

```
REFLECTED_NOTIFY_HANDLER( id, cd, func )
```

### <a name="parameters"></a>参数

*id*<br/>
中菜单项、控件或快捷键的标识符。

*cd*<br/>
中通知代码。

*func*<br/>
中消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="reflected_notify_id_handler"></a><a name="reflected_notify_id_handler"></a> REFLECTED_NOTIFY_ID_HANDLER

与 [NOTIFY_ID_HANDLER](#notify_id_handler)类似，但会映射从父窗口反射的通知。

```
REFLECTED_NOTIFY_ID_HANDLER( id, func )
```

### <a name="parameters"></a>参数

*id*<br/>
中菜单项、控件或快捷键的标识符。

*func*<br/>
中消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="reflected_notify_range_code_handler"></a><a name="reflected_notify_range_code_handler"></a> REFLECTED_NOTIFY_RANGE_CODE_HANDLER

与 [NOTIFY_RANGE_CODE_HANDLER](#notify_range_code_handler)类似，但会映射从父窗口反射的通知。

```
REFLECTED_NOTIFY_RANGE_CODE_HANDLER( idFirst, idLast, cd, func )
```

### <a name="parameters"></a>参数

*idFirst*<br/>
中标记连续的控件标识符范围的开头。

*idLast*<br/>
中标记连续的控件标识符范围的结尾。

*cd*<br/>
中通知代码。

*func*<br/>
中消息处理程序函数的名称。

### <a name="requirements"></a>要求

**标头：** atlwin。h

## <a name="reflected_notify_range_handler"></a><a name="reflected_notify_range_handler"></a> REFLECTED_NOTIFY_RANGE_HANDLER

与 [NOTIFY_RANGE_HANDLER](#notify_range_handler)类似，但会映射从父窗口反射的通知。

```
REFLECTED_NOTIFY_RANGE_HANDLER( idFirst, idLast, func )
```

### <a name="parameters"></a>参数

*idFirst*<br/>
中标记连续的控件标识符范围的开头。

*idLast*<br/>
中标记连续的控件标识符范围的结尾。

*func*<br/>
中消息处理程序函数的名称。

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)
