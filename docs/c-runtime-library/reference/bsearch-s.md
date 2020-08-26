---
title: bsearch_s
ms.date: 4/2/2020
api_name:
- bsearch_s
- _o_bsearch_s
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- bsearch_s
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch_s function
ms.assetid: d5690d5e-6be3-4f1d-aa0b-5ca6dbded276
ms.openlocfilehash: 20b4c482210f480730f7da4c89549d207ea6ca7d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845167"
---
# <a name="bsearch_s"></a>bsearch_s

执行排序数组的二进制搜索。 此函数是一种具有安全增强功能的 [bsearch](bsearch.md) 版本，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。

## <a name="syntax"></a>语法

```C
void *bsearch_s(
   const void *key,
   const void *base,
   size_t number,
   size_t width,
   int ( __cdecl *compare ) ( void *, const void *key, const void *datum),
   void * context
);
```

### <a name="parameters"></a>参数

*按键*\
指向要搜索的键的指针。

*基座*\
指向搜索数据的基的指针。

*多种*\
元素数量。

*宽度*\
元素的宽度。

*并排*\
比较两个元素的回调函数。 第一个参数是 *上下文* 指针。 第二个参数是指向搜索 *键* 的指针。 第三个参数是指向要与 *该键*进行比较的数组元素的指针。

*快捷*\
指向可在比较函数中访问的对象的指针。

## <a name="return-value"></a>返回值

**bsearch_s**返回一个指针，该指针指向由*base*指向的数组中的*键*的匹配项。 如果未找到 *键* ，则该函数返回 **NULL**。 如果数组不是以升序排序的，或包含具有相同键的重复记录，则不可预知结果。

如果向函数传递了无效参数，则它将调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将 **errno** 设置为 **EINVAL** ，并且该函数将返回 **NULL**。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

### <a name="error-conditions"></a>错误条件

|*键*|*base*|*并排*|*数字*|width |**`errno`**|
|-|-|-|-|-|-|
|**NULL**|any|any|any|any|**EINVAL**|
|any|**NULL**|any|!= 0|any|**EINVAL**|
|any|any|any|any|= 0|**EINVAL**|
|any|any|**NULL**|一个|any|**EINVAL**|

## <a name="remarks"></a>注解

**Bsearch_s**函数对*数字*元素的已排序数组执行二进制搜索，其中每个*宽度*字节大小均为大小。 *基值*是指向要搜索的数组的基的指针，而*键*是正在查找的值。 *Compare*参数是指向用户提供的例程的指针，它将所请求的密钥与数组元素进行比较，并返回以下指定其关系的值之一：

|*比较*例程返回的值|说明|
|-----------------------------------------|-----------------|
|\< 0|键小于数组元素。|
|0|键等于数组元素。|
|> 0|键大于数组元素。|

如果搜索的数据结构是对象的一部分，并且 compare 函数需要访问该对象的成员，则 *上下文* 指针可能会很有用。 *Compare*函数可以将 void 指针转换为适当的对象类型并访问该对象的成员。 添加 *上下文* 参数会使 **bsearch_s** 更安全，因为其他上下文可用于避免与使用静态变量关联的重入 bug，以使数据可供 *compare* 函数使用。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**bsearch_s**|\<stdlib.h> 和 \<search.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

此程序对具有 [qsort_s](qsort-s.md)的字符串数组进行排序，然后使用 bsearch_s 查找单词“cat”。

```cpp
// crt_bsearch_s.cpp
// This program uses bsearch_s to search a string array,
// passing a locale as the context.
// compile with: /EHsc
#include <stdlib.h>
#include <stdio.h>
#include <search.h>
#include <process.h>
#include <locale.h>
#include <locale>
#include <windows.h>
using namespace std;

// The sort order is dependent on the code page.  Use 'chcp' at the
// command line to change the codepage.  When executing this application,
// the command prompt codepage must match the codepage used here:

#define CODEPAGE_850

#ifdef CODEPAGE_850
#define ENGLISH_LOCALE "English_US.850"
#endif

#ifdef CODEPAGE_1252
#define ENGLISH_LOCALE "English_US.1252"
#endif

// The context parameter lets you create a more generic compare.
// Without this parameter, you would have stored the locale in a
// static variable, thus making it vulnerable to thread conflicts
// (if this were a multithreaded program).

int compare( void *pvlocale, char **str1, char **str2)
{
    char *s1 = *str1;
    char *s2 = *str2;

    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));

    return use_facet< collate<char> >(loc).compare(
       s1, s1+strlen(s1),
       s2, s2+strlen(s2) );
}

int main( void )
{
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};

   char *key = "cat";
   char **result;
   int i;

   /* Sort using Quicksort algorithm: */
   qsort_s( arr,
            sizeof(arr)/sizeof(arr[0]),
            sizeof( char * ),
            (int (*)(void*, const void*, const void*))compare,
            &locale(ENGLISH_LOCALE) );

   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */
      printf( "%s ", arr[i] );

   /* Find the word "cat" using a binary search algorithm: */
   result = (char **)bsearch_s( &key,
                                arr,
                                sizeof(arr)/sizeof(arr[0]),
                                sizeof( char * ),
                                (int (*)(void*, const void*, const void*))compare,
                                &locale(ENGLISH_LOCALE) );
   if( result )
      printf( "\n%s found at %Fp\n", *result, result );
   else
      printf( "\nCat not found!\n" );
}
```

```Output
cat cow dog goat horse human pig rat
cat found at 002F0F04
```

## <a name="see-also"></a>另请参阅

[搜索和排序](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
