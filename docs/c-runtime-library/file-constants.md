---
description: 了解更多：文件常量
title: 文件常量
ms.date: 11/04/2016
f1_keywords:
- _O_EXCL
- _O_RDWR
- _O_APPEND
- _O_RDONLY
- _O_TRUNC
- _O_CREAT
- _O_WRONLY
helpviewer_keywords:
- _O_RDWR constant
- O_EXCL constant
- O_RDWR constant
- O_WRONLY constant
- O_APPEND constant
- O_CREAT constant
- _O_CREAT constant
- _O_APPEND constant
- _O_EXCL constant
- O_TRUNC constant
- _O_RDONLY constant
- _O_TRUNC constant
- O_RDONLY constant
- _O_WRONLY constant
ms.assetid: c8fa5548-9ac2-4217-801d-eb45e86f2fa4
ms.openlocfilehash: a174a9bd8924f4d209f937187614863ce7111b3b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296597"
---
# <a name="file-constants"></a>文件常量

## <a name="syntax"></a>语法

```
#include <fcntl.h>
```

## <a name="remarks"></a>备注

由这些常量中的一个或多个常量构成的整数表达式确定允许进行的读取或写入操作的类型。 它是通过将一个或多个常量与平移模式常量组合来构成的。

文件常量如下所示：

|返回的常量|描述|
|-|-|
| `_O_APPEND`  | 在每次执行写入操作前，将文件指针重新定位到文件尾。  |
| `_O_CREAT`  | 创建一个文件并打开该文件以进行写入；如果有由 filename 指定的文件存在，则此操作不起作用。  |
| `_O_EXCL`  | 如果由 filename 指定的文件存在，则将返回一个错误值。 仅在与 `_O_CREAT` 一起使用时适用。  |
| `_O_RDONLY`  | 打开文件以仅供读取；如果提供此标志，则无法提供 `_O_RDWR` 和 `_O_WRONLY`。  |
| `_O_RDWR`  | 打开文件以供读取和写入；如果提供此标志，则无法提供 `_O_RDONLY` 和 `_O_WRONLY`。  |
| `_O_TRUNC`  | 打开现有文件并将其截断为零长度；此文件必须具有写入权限。 销毁此文件的内容。 如果提供此标志，则无法指定 `_O_RDONLY`。  |
| `_O_WRONLY`  | 打开文件以仅供写入；如果提供此标志，则无法提供 `_O_RDONLY` 和 `_O_RDWR`。  |

## <a name="see-also"></a>请参阅

[_open、_wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_sopen、_wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[全局常量](../c-runtime-library/global-constants.md)
