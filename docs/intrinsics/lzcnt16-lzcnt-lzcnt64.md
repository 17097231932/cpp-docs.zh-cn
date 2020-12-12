---
description: 了解详细信息： __lzcnt16、__lzcnt __lzcnt64
title: __lzcnt16、__lzcnt、__lzcnt64
ms.date: 09/02/2019
f1_keywords:
- __lzcnt64
- __lzcnt16
- __lzcnt
helpviewer_keywords:
- __lzcnt intrinsic
- lzcnt instruction
- lzcnt16 intrinsic
- lzcnt intrinsic
- __lzcnt16 intrinsic
- lzcnt64 intrinsic
- __lzcnt64 intrinsic
ms.assetid: 412113e7-052e-46e5-8bfa-d5ad72abc10e
ms.openlocfilehash: 75e2c105d05cfe4620f558a4f44c8ae8b9cd6f8f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167729"
---
# <a name="__lzcnt16-__lzcnt-__lzcnt64"></a>__lzcnt16、__lzcnt、__lzcnt64

**Microsoft 专用**

计算16、32或64位整数中的前导零的数目。

## <a name="syntax"></a>语法

```C
unsigned short __lzcnt16(
   unsigned short value
);
unsigned int __lzcnt(
   unsigned int value
);
unsigned __int64 __lzcnt64(
   unsigned __int64 value
);
```

### <a name="parameters"></a>parameters

*负值*\
中用于扫描前导零的16、32或64位无符号整数。

## <a name="return-value"></a>返回值

参数中前导零位的数目 `value` 。 如果 `value` 为零，则返回值为输入操作数 (16、32或 64) 的大小。 如果的最高有效位 `value` 为1，则返回值为零。

## <a name="requirements"></a>要求

|Intrinsic|体系结构|
|---------------|------------------|
|`__lzcnt16`|AMD：高级位操作 (ABM) <br /><br /> Intel： Haswell|
|`__lzcnt`|AMD：高级位操作 (ABM) <br /><br /> Intel： Haswell|
|`__lzcnt64`|AMD：在64位模式下 (ABM) 的高级位操作。<br /><br /> Intel： Haswell|

**头文件** \<intrin.h>

## <a name="remarks"></a>备注

每个内部函数都会生成 `lzcnt` 指令。  指令返回的值的大小与 `lzcnt` 参数的大小相同。  在32位模式下，没有任何64位通用寄存器，因此 `lzcnt` 不支持64位。

若要确定指令的硬件支持 `lzcnt` ，请调用 `__cpuid` 内部， `InfoType=0x80000001` 并检查的第5位 `CPUInfo[2] (ECX)` 。 如果支持指令，则此位为 1; 否则为0。 如果在不支持指令的硬件上运行使用内部函数的代码 `lzcnt` ，则结果是不可预知的。

在不支持指令的 Intel 处理器上 `lzcnt` ，指令字节编码将作为 `bsr` (位扫描反向) 来执行。 如果需要考虑代码可移植性，请改为考虑使用 `_BitScanReverse` 内部函数。 有关详细信息，请参阅 [_BitScanReverse _BitScanReverse64](../intrinsics/bitscanreverse-bitscanreverse64.md)。

## <a name="example"></a>示例

```cpp
// Compile this test with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
  unsigned short us[3] = {0, 0xFF, 0xFFFF};
  unsigned short usr;
  unsigned int   ui[4] = {0, 0xFF, 0xFFFF, 0xFFFFFFFF};
  unsigned int   uir;

  for (int i=0; i<3; i++) {
    usr = __lzcnt16(us[i]);
    cout << "__lzcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;
  }

  for (int i=0; i<4; i++) {
    uir = __lzcnt(ui[i]);
    cout << "__lzcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;
  }
}
```

```Output
__lzcnt16(0x0) = 16
__lzcnt16(0xff) = 8
__lzcnt16(0xffff) = 0
__lzcnt(0x0) = 32
__lzcnt(0xff) = 24
__lzcnt(0xffff) = 16
__lzcnt(0xffffffff) = 0
```

**结束 Microsoft 专用**

本内容的部分内容为高级微设备，Inc. 的版权2007。保留所有权利。 从高级微设备，Inc. 的权限重现。

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
