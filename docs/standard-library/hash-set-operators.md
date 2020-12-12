---
description: 了解详细信息： &lt; hash_set &gt; 运算符
title: '&lt;hash_set&gt; 运算符'
ms.date: 03/27/2019
f1_keywords:
- hash_set/std::operator!=
- hash_set/std::operator==
ms.assetid: 403d8e4e-0b3f-43fb-bc5a-8100c4f331c5
ms.openlocfilehash: a52c749df2bdd690fcd936c9a361251728696ccd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324078"
---
# <a name="lthash_setgt-operators"></a>&lt;hash_set&gt; 运算符

[operator！ =](#op_neq)\
[operator！ = (hash_multiset) ](#op_neq_hash_multiset)\
[operator = =](#op_eq_eq)\
[operator = = (hash_multiset) ](#op_eq_eq_hash_multiset)

## <a name="operator"></a><a name="op_neq"></a> operator！ =

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。

测试运算符左侧的 hash_set 对象是否不等于右侧的 hash_set 对象。

```cpp
bool operator!=(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左中*\
一个 `hash_set` 类型的对象。

*然后*\
一个 `hash_set` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果 hash_sets 不相等，则为; 否则为。 **`false`** 如果 hash_sets 相等，则为。

### <a name="remarks"></a>备注

hash_set 对象之间的比较基于其元素的成对比较。 如果两个 hash_set 具有的元素数目相等且对应元素具有相同的值，则这两个 hash_set 相等。 否则，它们不相等。

<的成员 [ hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件位于 [stdext 命名空间](../standard-library/stdext-namespace.md)中。

### <a name="example"></a>示例

```cpp
// hash_set_op_ne.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2, hs3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hs1.insert ( i );
      hs2.insert ( i * i );
      hs3.insert ( i );
   }

   if ( hs1 != hs2 )
      cout << "The hash_sets hs1 and hs2 are not equal." << endl;
   else
      cout << "The hash_sets hs1 and hs2 are equal." << endl;

   if ( hs1 != hs3 )
      cout << "The hash_sets hs1 and hs3 are not equal." << endl;
   else
      cout << "The hash_sets hs1 and hs3 are equal." << endl;
}
```

```Output
The hash_sets hs1 and hs2 are not equal.
The hash_sets hs1 and hs3 are equal.
```

## <a name="operator"></a><a name="op_eq_eq"></a> operator = =

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。

测试运算符左侧的 hash_set 对象是否等于右侧的 hash_set 对象。

```cpp
bool operator!==(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左中*\
一个 `hash_set` 类型的对象。

*然后*\
一个 `hash_set` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的 hash_set 等于运算符右侧的 hash_set，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

hash_set 对象之间的比较基于其元素的成对比较。 如果两个 hash_set 具有的元素数目相等且对应元素具有相同的值，则这两个 hash_set 相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// hash_set_op_eq.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The hash_sets s1 and s2 are equal." << endl;
   else
      cout << "The hash_sets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The hash_sets s1 and s3 are equal." << endl;
   else
      cout << "The hash_sets s1 and s3 are not equal." << endl;
}
```

```Output
The hash_sets s1 and s2 are not equal.
The hash_sets s1 and s3 are equal.
```

## <a name="operator-hash_multiset"></a><a name="op_neq_hash_multiset"></a> operator！ = (hash_multiset) 

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。

测试运算符左侧的 hash_multiset 对象是否不等于右侧的 hash_multiset 对象。

```cpp
bool operator!=(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左中*\
一个 `hash_multiset` 类型的对象。

*然后*\
一个 `hash_multiset` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果 hash_multisets 不相等，则为; 否则为。 **`false`** 如果 hash_multisets 相等，则为。

### <a name="remarks"></a>备注

hash_multiset 对象之间的比较基于其元素的成对比较。 如果两个 hash_multiset 具有的元素数目相等且对应元素具有相同的值，则这两个 hash_multiset 相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// hashset_op_ne.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1, hs2, hs3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hs1.insert ( i );
      hs2.insert ( i * i );
      hs3.insert ( i );
   }

   if ( hs1 != hs2 )
      cout << "The hash_multisets hs1 and hs2 are not equal." << endl;
   else
      cout << "The hash_multisets hs1 and hs2 are equal." << endl;

   if ( hs1 != hs3 )
      cout << "The hash_multisets hs1 and hs3 are not equal." << endl;
   else
      cout << "The hash_multisets hs1 and hs3 are equal." << endl;
}
```

```Output
The hash_multisets hs1 and hs2 are not equal.
The hash_multisets hs1 and hs3 are equal.
```

## <a name="operator-hash_multiset"></a><a name="op_eq_eq_hash_multiset"></a> operator = = (hash_multiset) 

> [!NOTE]
> 此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。

测试运算符左侧的 hash_multiset 对象是否等于右侧的 hash_multiset 对象。

```cpp
bool operator!==(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左中*\
一个 `hash_multiset` 类型的对象。

*然后*\
一个 `hash_multiset` 类型的对象。

### <a name="return-value"></a>返回值

**`true`** 如果运算符左侧的 hash_multiset 等于运算符右侧的 hash_multiset，则为; 否则为。否则为 **`false`** 。

### <a name="remarks"></a>备注

hash_multiset 对象之间的比较基于其元素的成对比较。 如果两个 hash_multiset 具有的元素数目相等且对应元素具有相同的值，则这两个 hash_multiset 相等。 否则，它们不相等。

### <a name="example"></a>示例

```cpp
// hash_multiset_op_eq.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The hash_multisets s1 and s2 are equal." << endl;
   else
      cout << "The hash_multisets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The hash_multisets s1 and s2 are equal." << endl;
   else
      cout << "The hash_multisets s1 and s2 are not equal." << endl;
}
```

```Output
The hash_multisets s1 and s2 are not equal.
The hash_multisets s1 and s2 are equal.
```

## <a name="see-also"></a>请参阅

[<hash_set>](../standard-library/hash-set.md)
