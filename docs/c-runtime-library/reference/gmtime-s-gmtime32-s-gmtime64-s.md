---
description: 詳細については、「gmtime_s、_gmtime32_s、_gmtime64_s」を参照してください。
title: gmtime_s、_gmtime32_s、_gmtime64_s
ms.date: 4/2/2020
api_name:
- _gmtime32_s
- gmtime_s
- _gmtime64_s
- _o__gmtime32_s
- _o__gmtime64_s
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
- _gmtime_s
- gmtime64_s
- gmtime32_s
- _gmtime64_s
- gmtime_s
- _gmtime32_s
helpviewer_keywords:
- gmtime_s function
- gmtime32_s function
- time functions
- gmtime64_s function
- _gmtime64_s function
- time structure conversion
- _gmtime_s function
- _gmtime32_s function
ms.assetid: 261c7df0-2b0c-44ba-ba61-cb83efaec60f
ms.openlocfilehash: bffe11bd655ed8cfead6b862abf0237270c3af20
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296460"
---
# <a name="gmtime_s-_gmtime32_s-_gmtime64_s"></a>gmtime_s、_gmtime32_s、_gmtime64_s

時刻値を **tm** 構造体に変換します。 これらは、「[Security Features in the CRT](../../c-runtime-library/security-features-in-the-crt.md)」 (CRT のセキュリティ機能) で説明されているように、セキュリティが強化されたバージョンの [_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md) です。

## <a name="syntax"></a>構文

```C
errno_t gmtime_s(
   struct tm* tmDest,
   const __time_t* sourceTime
);
errno_t _gmtime32_s(
   struct tm* tmDest,
   const __time32_t* sourceTime
);
errno_t _gmtime64_s(
   struct tm* tmDest,
   const __time64_t* sourceTime
);
```

### <a name="parameters"></a>パラメーター

*tmDest*<br/>
[Tm](../../c-runtime-library/standard-types.md)構造体へのポインター。 返される構造体のフィールドは、 *タイマー* 引数の評価値を現地時刻ではなく UTC で保持します。

*sourceTime*<br/>
格納されている時刻へのポインター。 時刻は、世界協定時刻 (UTC: Coordinated Universal Time) の 1970 年 1 月 1 日の深夜 00:00:00 から経過した時間 (秒単位) を表します。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。 障害が発生した場合、戻り値はエラー コードを示します。 エラーコードは Errno に定義されています。これらのエラーの一覧については、「 [errno](../../c-runtime-library/errno-constants.md)」を参照してください。

### <a name="error-conditions"></a>エラー条件

|*tmDest*|*sourceTime*|戻り値|*Tmdest* の値|
|-----------|------------|------------|--------------------|
|**NULL**|any|**EINVAL**|変更されません。|
|Not **NULL** (有効なメモリを指す)|**NULL**|**EINVAL**|すべてのフィールドが-1 に設定されます。|
|**NULL** 以外|< 0|**EINVAL**|すべてのフィールドが-1 に設定されます。|

最初の 2 つのエラーの場合は、「[Parameter Validation](../../c-runtime-library/parameter-validation.md)」 (パラメーターの検証) に説明されているとおり、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は **errno** を **einval** に設定し、 **einval** を返します。

## <a name="remarks"></a>解説

**_Gmtime32_s** 関数は、 *sourcetime* 値を分割し、time. h で定義されている **tm** 型の構造に格納します。 構造体のアドレスは、 *Tmdest* で渡されます。 *Sourcetime* の値は、通常、 [time](time-time32-time64.md)関数の呼び出しから取得されます。

> [!NOTE]
> 対象の環境によって、夏時間が有効かどうか判断されます。 C ランタイム ライブラリでは、アメリカ合衆国の規則を前提に夏時間を計算します。

**`int`** 次の表に示すように、構造体の各フィールドの型はです。

|フィールド|説明|
|-|-|
|**tm_sec**|秒後 (0-59)。|
|**tm_min**|分後 (0-59)。|
|**tm_hour**|深夜からの時間 (0-23)。|
|**tm_mday**|月の通算日 (1-31)。|
|**tm_mon**|月 (0-11;1月 = 0)。|
|**tm_year**|年 (実際の西暦から 1900 を引いた数)|
|**tm_wday**|曜日 (0-6;日曜日 = 0)。|
|**tm_yday**|年の通算日 (0-365;1月1日 = 0)。|
|**tm_isdst**|**Gmtime_s** の場合は常に0です。|

**__time64_t** 構造体を使用する **_gmtime64_s** では、23:59:59 年12月 31 3000 日までの日付を表すことができます。**gmtime32_s** は、2038年1月18日23:59:59 までの日付のみを表します。 これらの関数の日付範囲の下限は、どちらも 1970 年 1 月 1 日の午前 0 時です。

**gmtime_s** は **_gmtime64_s** に評価されるインライン関数であり、 **time_t** は **__time64_t** に相当します。 以前の32ビット **time_t** として **time_t** を解釈するようにコンパイラに強制する必要がある場合は **_USE_32BIT_TIME_T** を定義できます。 これにより、 **gmtime_s** が **_gmtime32_s** にインラインで配置されます。 この方法はお勧めしません。2038 年 1 月 18 日より後にアプリケーションがエラーになる可能性があり、また、64 ビット プラットフォームでは使用できないためです。

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須の C ヘッダー|必須の C++ ヘッダー|
|-------------|---------------------|-|
|**gmtime_s**、 **_gmtime32_s**、 **_gmtime64_s**|\<time.h>|\<ctime> または \<time.h>|

互換性について詳しくは、「 [Compatibility](../../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="example"></a>例

```C
// crt_gmtime64_s.c
// This program uses _gmtime64_s to convert a 64-bit
// integer representation of coordinated universal time
// to a structure named newtime, then uses asctime_s to
// convert this structure to an output string.

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm newtime;
   __int64 ltime;
   char buf[26];
   errno_t err;

   _time64( &ltime );

   // Obtain coordinated universal time:
   err = _gmtime64_s( &newtime, &ltime );
   if (err)
   {
      printf("Invalid Argument to _gmtime64_s.");
   }

   // Convert to an ASCII representation
   err = asctime_s(buf, 26, &newtime);
   if (err)
   {
      printf("Invalid Argument to asctime_s.");
   }

   printf( "Coordinated universal time is %s\n",
           buf );
}
```

```Output
Coordinated universal time is Fri Apr 25 20:12:33 2003
```

## <a name="see-also"></a>関連項目

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[_mkgmtime、_mkgmtime32、_mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
