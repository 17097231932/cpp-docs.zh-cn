---
description: 了解详细信息： _bstr_t：： operator =
title: _bstr_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator=
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
ms.openlocfilehash: 78447048a45567df603acf3af0bc51cefbdb187d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97308778"
---
# <a name="_bstr_toperator-"></a>_bstr_t::operator =

**Microsoft 专用**

将新值赋给现有 `_bstr_t` 对象。

## <a name="syntax"></a>语法

```
_bstr_t& operator=(const _bstr_t& s1) throw ( );
_bstr_t& operator=(const char* s2);
_bstr_t& operator=(const wchar_t* s3);
_bstr_t& operator=(const _variant_t& var);
```

#### <a name="parameters"></a>parameters

s1<br/>
将分配给现有 `_bstr_t` 对象的 `_bstr_t` 对象。

*s2*<br/>
将分配给现有 `_bstr_t` 对象的多字节字符串。

*s3*<br/>
将分配给现有 `_bstr_t` 对象的 Unicode 字符串。

*var*<br/>
将分配给现有 `_variant_t` 对象的 `_bstr_t` 对象。

**结束 Microsoft 专用**

## <a name="example"></a>示例

有关使用 **operator =** 的示例，请参阅 [_Bstr_t：： Assign](../cpp/bstr-t-assign.md) 。

## <a name="see-also"></a>请参阅

[_bstr_t 类](../cpp/bstr-t-class.md)
