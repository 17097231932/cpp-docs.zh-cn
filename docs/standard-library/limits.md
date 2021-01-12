---
description: 了解详细信息： &lt; 限制&gt;
title: '&lt;limits&gt;'
ms.date: 11/04/2016
f1_keywords:
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: 23601b4b7f7ea06071a6b1f5fbd87ce0a0babce3
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126385"
---
# <a name="ltlimitsgt"></a>&lt;limits&gt;

定义类模板 `numeric_limits` ，以及两个有关浮点表示形式和舍入的枚举。

## <a name="requirements"></a>要求

**标头：**\<limits>

**命名空间:** std

## <a name="remarks"></a>备注

类的显式专用化 `numeric_limits` 描述基本类型（包括字符、整数和浮点类型）的许多属性， **`bool`** 这些属性是实现定义的，而不是由 c + + 语言的规则修复的。 中描述的属性 \<limits> 包括准确性、最小值和最大大小表示形式、舍入和信号类型错误。

## <a name="members"></a>成员

### <a name="enumerations"></a>枚举

|名称|描述|
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|此枚举描述实现可以选择用于表示非标准化浮点值的各种方法，这种浮点值由于太小而无法表示为规范化值：|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|此枚举描述实现可以选择用于将浮点值舍入为整数值的各种方法。|

### <a name="classes"></a>类

|“属性”|描述|
|-|-|
|[numeric_limits 类](../standard-library/numeric-limits-class.md)|类模板描述内置数值类型的算术属性。|

## <a name="see-also"></a>另请参阅

[标头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
