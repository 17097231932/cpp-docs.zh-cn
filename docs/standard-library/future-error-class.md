---
description: 了解详细信息： future_error 类
title: future_error 类
ms.date: 11/04/2016
f1_keywords:
- future/std::future_error
ms.assetid: 6071c545-ac2a-49ef-9967-07b0125da861
ms.openlocfilehash: c7dc99ea842cd13658c13a5c2492bda3d853302f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324208"
---
# <a name="future_error-class"></a>future_error 类

描述可由管理 [future](../standard-library/future-class.md) 对象的类型方法引发的异常对象。

## <a name="syntax"></a>语法

```cpp
class future_error : public logic_error {
public:
    future_error(error_code code);

const error_code& code() const throw();

const char *what() const throw();

};
```

## <a name="requirements"></a>要求

**标头：**\<future>

**命名空间:** std

## <a name="see-also"></a>请参阅

[标头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[logic_error 类](../standard-library/logic-error-class.md)\
[error_code 类](../standard-library/error-code-class.md)
