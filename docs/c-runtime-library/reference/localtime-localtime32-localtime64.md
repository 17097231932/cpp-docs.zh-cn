---
description: 了解详细信息： localtime、_localtime32、_localtime64
title: localtime、_localtime32、_localtime64
ms.date: 4/2/2020
api_name:
- _localtime64
- _localtime32
- localtime
- _o__localtime32
- _o__localtime64
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- localtime64
- _localtime64
- localtime32
- localtime
- _localtime32
helpviewer_keywords:
- localtime32 function
- _localtime32 function
- _localtime64 function
- localtime64 function
- localtime function
- time, converting values
ms.assetid: 4260ec3d-43ee-4538-b998-402a282bb9b8
ms.openlocfilehash: e19e419be52788bfd0e4f4a67c72ef8a6737993e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326290"
---
# <a name="localtime-_localtime32-_localtime64"></a>localtime、_localtime32、_localtime64

转换时间值并更正本地时区。 这些函数的更安全版本已经可用；请参阅 [localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)。

## <a name="syntax"></a>语法

```C
struct tm *localtime( const time_t *sourceTime );
struct tm *_localtime32( const __time32_t *sourceTime );
struct tm *_localtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>parameters

*sourceTime*<br/>
指向存储时间的指针。

## <a name="return-value"></a>返回值

返回指向结构结果的指针; 如果传递到函数的日期为，则返回 **NULL** 。

- 1970 年 1 月 1 日午夜前。

- 03:14:07，年1月 2038 19 日， (使用 **_time32** 和 **time32_t**) 。

- 23:59:59 年12月 3000 31 日， (使用 **_time64** 和 **__time64_t**) 。

使用 **__time64_t** 结构的 **_localtime64** 允许日期在23:59:59 年12月31日3000、协调世界时 (UTC) 上表示，而 **_localtime32** 表示日期到23:59:59 年1月18日（2038，utc）。

**localtime** 是一个计算结果为 **_localtime64**， **time_t** 等效于 **__time64_t** 的内联函数。 如果需要强制编译器将 **time_t** 解释为旧32位 **time_t**，可以定义 **_USE_32BIT_TIME_T**。 这样做会导致 **localtime** 计算 **_localtime32**。 不建议这样做，因为应用程序可能会在 2038 年 1 月 18 日后失效；且在 64 位平台上不允许使用它。

结构类型 [tm](../../c-runtime-library/standard-types.md) 的字段存储以下值，其中每个值都是 **`int`** ：

|字段|描述|
|-|-|
|**tm_sec**|分钟 (0-59) 之后的秒数。|
|**tm_min**| (0-59) 后的分钟数。|
|**tm_hour**|自午夜 (0-23) 。|
|**tm_mday**|月 (1-31) 的第几天。|
|**tm_mon**|月 (0-11;1月 = 0) 。|
|**tm_year**|年（当前年份减去 1900）。|
|**tm_wday**|星期几 (0-6;星期日 = 0) 。|
|**tm_yday**|0-365 年的某一日 (;1月1日 = 0) 。|
|**tm_isdst**|如果夏令时生效，则为正值；如果夏令时不生效，则为 0；如果夏令时状态未知，则为负值。|

如果设置了 **TZ** 环境变量，C 运行时库将假定美国适用于实现夏令时 (DST) 计算的规则。

## <a name="remarks"></a>备注

**Localtime** 函数将存储的时间转换为 [time_t](../../c-runtime-library/standard-types.md)值，并将结果存储在类型为 [tm](../../c-runtime-library/standard-types.md)的结构中。 **`long`** 值 *sourceTime* 表示自00:00:00 年1月 1970 1 日午夜 () 午夜起经过的秒数。 此值通常是从 [time](time-time32-time64.md) 函数获取的。

32位和64位版本的 [gmtime](gmtime-gmtime32-gmtime64.md)、 [mktime](mktime-mktime32-mktime64.md)、 [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)和 **localtime** 都为转换使用单个 **tm** 结构（每个线程）。 每次调用这些例程都会破坏上一次调用的结果。

如果用户首先设置全局环境变量 **TZ**，则 **localtime** 会纠正本地时区。 设置了 **TZ** 后，还会自动设置另外三个 (**_timezone**、 **_daylight** 和 **_tzname**) 的环境变量。 如果未设置 **TZ** 变量， **localtime** 将尝试使用 "控制面板" 的 "日期/时间" 应用程序中指定的时区信息。 如果无法获取此信息，则它默认使用代表太平洋时区的 PST8PDT。 有关这些变量的说明，请参阅 [_tzset](tzset.md)。 **TZ** 是 Microsoft 扩展，而不是 **localtime** 的 ANSI 标准定义的一部分。

> [!NOTE]
> 目标环境应尝试确定夏令时是否生效。

这些函数验证其参数。 如果 *sourceTime* 为 null 指针，或 *sourceTime* 值为负，则这些函数将调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则函数将返回 **NULL** ，并将 **Errno** 设置为 **EINVAL**。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅 [CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的 C 标头|必需的 C++ 标头|
|-------------|---------------------|-|
|**localtime**、 **_localtime32**、 **_localtime64**|\<time.h>|\<ctime> 或 \<time.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_localtime.cpp
// compile with: /W3
// This program uses _time64 to get the current time
// and then uses localtime64() to convert this time to a structure
// representing the local time. The program converts the result
// from a 24-hour clock to a 12-hour clock and determines the
// proper extension (AM or PM).

#include <stdio.h>
#include <string.h>
#include <time.h>

int main( void )
{
    struct tm *newtime;
    char am_pm[] = "AM";
    __time64_t long_time;

    _time64( &long_time );             // Get time as 64-bit integer.
                                       // Convert to local time.
    newtime = _localtime64( &long_time ); // C4996
    // Note: _localtime64 deprecated; consider _localetime64_s

    if( newtime->tm_hour > 12 )        // Set up extension.
        strcpy_s( am_pm, sizeof(am_pm), "PM" );
    if( newtime->tm_hour > 12 )        // Convert from 24-hour
        newtime->tm_hour -= 12;        //   to 12-hour clock.
    if( newtime->tm_hour == 0 )        // Set hour to 12 if midnight.
        newtime->tm_hour = 12;

    char buff[30];
    asctime_s( buff, sizeof(buff), newtime );
    printf( "%.19s %s\n", buff, am_pm );
}
```

```Output
Tue Feb 12 10:05:58 AM
```

## <a name="see-also"></a>请参阅

[时间管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
