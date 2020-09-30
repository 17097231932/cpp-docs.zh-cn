---
title: 编译器错误 C3345
ms.date: 11/04/2016
f1_keywords:
- C3345
helpviewer_keywords:
- C3345
ms.assetid: 1dda4c79-73bb-441b-b939-746154c3afba
ms.openlocfilehash: 8682069fdf719f4e85d1d6f5107de1903e3ae071
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504849"
---
# <a name="compiler-error-c3345"></a>编译器错误 C3345

“identifier”：模块名称的标识符无效

模块的 *标识符* 包含一个或多个不可接受的字符。 如果第一个字符是字母、下划线或高 ANSI (0x80 FF) 字符，且后续字符是字母数字、下划线或高 ANSI 字符，则标识符有效。

### <a name="to-correct-this-error"></a>更正此错误

1. 确保 *标识符* 不包含空格或其他不可接受的字符。

## <a name="example"></a>示例

下面的代码示例会导致错误消息 C3345，因为 `name` 特性的 `module` 参数包含一个空格。

```cpp
// cpp_attr_name_module.cpp
// compile with: /LD /link /OPT:NOREF
#include <atlbase.h>
#include <atlcom.h>
#include <atlwin.h>
#include <atltypes.h>
#include <atlctl.h>
#include <atlhost.h>
#include <atlplus.h>

// C3345 expected
[module(dll, name="My Library", version="1.2", helpfile="MyHelpFile")]
// Try the following line instead
//[module(dll, name="MyLibrary", version="1.2", helpfile="MyHelpFile")]
// Module attribute now applies to this class
class CMyClass {
public:
BOOL WINAPI DllMain(DWORD dwReason, LPVOID lpReserved) {
   // add your own code here
   return __super::DllMain(dwReason, lpReserved);
   }
};
```

## <a name="see-also"></a>请参阅

[__iscsym](../../c-runtime-library/reference/iscsym-functions.md)<br/>
[字符分类](../../c-runtime-library/character-classification.md)<br/>
[模块](../../windows/attributes/module-cpp.md)
