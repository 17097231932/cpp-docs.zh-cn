---
description: 了解详细信息： &lt; 执行&gt;
title: '&lt;操作&gt;'
ms.date: 04/18/2019
f1_keywords:
- <execution>
- std::<execution>
helpviewer_keywords:
- execution header
ms.openlocfilehash: ea444ab2f4fcf3211e85837701a8ea6a0c3ec81f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324404"
---
# <a name="ltexecutiongt"></a>&lt;操作&gt;

介绍并行算法的执行策略。

## <a name="syntax"></a>语法

```
namespace std {
    template<class T> inline constexpr bool is_execution_policy_v = is_execution_policy<T>::value;
}
namespace std::execution {
    inline constexpr sequenced_policy seq { unspecified };
    inline constexpr parallel_policy par { unspecified };
    inline constexpr parallel_unsequenced_policy par_unseq { unspecified };
}
```

### <a name="classes-and-structs"></a>类和结构

|名称|描述|
|-|-|
|[is_execution_policy 结构](is-execution-policy-struct.md)|检测执行策略，以排除其他不明确的重载决策参与的函数签名。|
|[parallel_policy 类](parallel-policy-class.md)|用作消除并行算法重载的唯一类型，并指示并行算法的执行可能会并行化。|
|[parallel_unsequenced_policy 类](parallel-unsequenced-policy-class.md)|用作消除并行算法重载的唯一类型，并指示并行算法的执行可能会并行化并向量化。|
|[sequenced_policy 类](sequenced-policy-class.md)|用作消除并行算法重载的唯一类型，并要求并行算法的执行不会并行化。|

## <a name="requirements"></a>要求

**标头：**\<execution>

**命名空间：** stdext

## <a name="see-also"></a>请参阅

[标头文件引用](cpp-standard-library-header-files.md)\
[C + + 标准库中的线程安全](thread-safety-in-the-cpp-standard-library.md)\
[C + + 标准库参考](cpp-standard-library-reference.md)
