---
description: 詳細については、_findfirst、_findfirst32、_findfirst32i64、_findfirst64、_findfirst64i32、_findfirsti64、_wfindfirst、_wfindfirst32、_wfindfirst32i64、_wfindfirst64、_wfindfirst64i32、_wfindfirsti64 を参照してください。
title: _findfirst、_findfirst32、_findfirst32i64、_findfirst64、_findfirst64i32、_findfirsti64、_wfindfirst、_wfindfirst32、_wfindfirst32i64、_wfindfirst64、_wfindfirst64i32、_wfindfirsti64
ms.date: 4/2/2020
api_name:
- _findfirst
- _wfindfirst
- _findfirst32
- _wfindfirst32
- _findfirst32i64
- _wfindfirst32i64
- _findfirst64
- _wfindfirst64
- _findfirst64i32
- _wfindfirst64i32
- _findfirsti64
- _wfindfirsti64
- _o__findfirst32
- _o__findfirst32i64
- _o__findfirst64
- _o__findfirst64i32
- _o__wfindfirst32
- _o__wfindfirst32i64
- _o__wfindfirst64
- _o__wfindfirst64i32
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- findfirst32i64
- wfindfirst32i64
- tfindfirst64
- _findfirst64i32
- _wfindfirst32i64
- _wfindfirsti64
- wfindfirst
- _tfindfirsti64
- findfirst32
- _tfindfirst32
- _findfirsti64
- findfirst
- wfindfirst64
- wfindfirst32
- tfindfirst32
- _wfindfirst64i32
- findfirst64i32
- tfindfirst64i32
- _wfindfirst
- findfirsti64
- _findfirst32i64
- wfindfirst64i32
- _wfindfirst32
- _findfirst32
- _tfindfirst32i64
- tfindfirst
- _tfindfirst64i32
- findfirst64
- _tfindfirst
- _findfirst64
- _tfindfirst64
- tfindfirst32i64
- _findfirst
- _wfindfirst64
helpviewer_keywords:
- _tfindfirst64 function
- _wfindfirst64i32 function
- _wfindfirst32i64 function
- wfindfirst32 function
- _findfirst function
- wfindfirst64 function
- _wfindfirst function
- _findfirst64i32 function
- wfindfirst function
- _findfirst64 function
- tfindfirst32 function
- _tfindfirst64i32 function
- findfirst function
- findfirst32i64 function
- tfindfirst64 function
- _tfindfirst32 function
- tfindfirst32i64 function
- tfindfirst64i32 function
- _wfindfirsti64 function
- _findfirst32i64 function
- findfirst32 function
- findfirsti64 function
- findfirst64i32 function
- tfindfirsti64 function
- tfindfirst function
- _wfindfirst32 function
- wfindfirsti64 function
- _tfindfirsti64 function
- _tfindfirst function
- _tfindfirst32i64 function
- findfirst64 function
- _findfirst32 function
- _findfirsti64 function
- wfindfirst32i64 function
- wfindfirst64i32 function
- _wfindfirst64 function
ms.assetid: 9bb46d1a-b946-47de-845a-a0b109a33ead
ms.openlocfilehash: dce0c283a6177940019f1d358bd6cfa500c04306
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263141"
---
# <a name="_findfirst-_findfirst32-_findfirst32i64-_findfirst64-_findfirst64i32-_findfirsti64-_wfindfirst-_wfindfirst32-_wfindfirst32i64-_wfindfirst64-_wfindfirst64i32-_wfindfirsti64"></a>_findfirst、_findfirst32、_findfirst32i64、_findfirst64、_findfirst64i32、_findfirsti64、_wfindfirst、_wfindfirst32、_wfindfirst32i64、_wfindfirst64、_wfindfirst64i32、_wfindfirsti64

*Filespec* 引数で指定されたファイルと一致するファイル名の最初のインスタンスに関する情報を指定します。

## <a name="syntax"></a>構文

```C
intptr_t _findfirst(
   const char *filespec,
   struct _finddata_t *fileinfo
);
intptr_t _findfirst32(
   const char *filespec,
   struct _finddata32_t *fileinfo
);
intptr_t _findfirst64(
   const char *filespec,
   struct _finddata64_t *fileinfo
);
intptr_t _findfirsti64(
   const char *filespec,
   struct _finddatai64_t *fileinfo
);
intptr_t _findfirst32i64(
   const char *filespec,
   struct _finddata32i64_t *fileinfo
);
intptr_t _findfirst64i32(
   const char *filespec,
   struct _finddata64i32_t *fileinfo
);
intptr_t _wfindfirst(
   const wchar_t *filespec,
   struct _wfinddata_t *fileinfo
);
intptr_t _wfindfirst32(
   const wchar_t *filespec,
   struct _wfinddata32_t *fileinfo
);
intptr_t _wfindfirst64(
   const wchar_t *filespec,
   struct _wfinddata64_t *fileinfo
);
intptr_t _wfindfirsti64(
   const wchar_t *filespec,
   struct _wfinddatai64_t *fileinfo
);
intptr_t _wfindfirst32i64(
   const wchar_t *filespec,
   struct _wfinddata32i64_t *fileinfo
);
intptr_t _wfindfirst64i32(
   const wchar_t *filespec,
   struct _wfinddata64i32_t *fileinfo
);
```

### <a name="parameters"></a>パラメーター

*側*<br/>
ターゲット ファイルの指定 (ワイルドカード文字を含めることができます)。

*fileinfo*<br/>
ファイル情報バッファー。

## <a name="return-value"></a>戻り値

正常に実行された場合、 **_findfirst** は、 *filespec* 仕様に一致するファイルまたはファイルのグループを識別する一意の検索ハンドルを返します。これは、以降の [_findnext](findnext-functions.md) また [_findclose](findclose.md)はの呼び出しで使用できます。 それ以外の場合、 **_findfirst** は-1 を返し、 **errno** を次のいずれかの値に設定します。

| errno の値 | 条件 |
|-|-|
| **EINVAL** | 無効なパラメーター: *filespec* または *fileinfo* が **NULL** でした。 または、オペレーティング システムが予期しないエラーを返しました。 |
| **ENOENT** | 一致しないファイルの指定。 |
| **ENOMEM** | メモリ不足です。 |
| **EINVAL** | ファイル名の指定が無効であるか、指定されたファイル名が **MAX_PATH** を超えています。 |

リターン コードの詳細については、「[_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

無効なパラメーターが渡されると、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、これらの関数は無効パラメーター ハンドラーを呼び出します。

## <a name="remarks"></a>解説

**_Findfirst** または [_findnext](findnext-functions.md)関数 (または variant) のいずれかを使用して終了した後、 [_findclose](findclose.md)を呼び出す必要があります。 呼び出すと、アプリケーション内でこれらの関数が使用しているリソースが解放されます。

**W** プレフィックスを持つこれらの関数のバリエーションは、ワイド文字バージョンです。それ以外の場合は、対応する1バイト関数と同じです。

これらの関数のバリエーションは、32 ビットや 64 ビットの時刻型と、32 ビットや 64 ビットのファイル サイズをサポートします。 最初の数値サフィックス (**32** または **64**) は、時刻型のサイズを示します。2番目のサフィックスは、 **i32** または **i64** のいずれかで、ファイルサイズが32ビットまたは64ビットの整数として表されるかどうかを示します。 32 ビットと 64 ビットの時刻型とファイル サイズをサポートするバージョンについては、次の表を参照してください。 **I32** または **i64** サフィックスは、time 型のサイズと同じ場合は省略されます。そのため **_findfirst64** 64 ビットのファイル長もサポートされ、 **_findfirst32** は32ビットのファイルの長さのみをサポートします。

これらの関数は、 *fileinfo* パラメーターに対してさまざまな形式の **_finddata_t** 構造を使用します。 構造体の詳細については、「[ファイル名検索関数](../../c-runtime-library/filename-search-functions.md)」を参照してください。

64 ビットの時刻型を使用するバリエーションでは、3000 年 12 月 31 日 23:59:59 (UTC) までのファイルの作成日を表現できます。 32 ビットの時刻型を使用するバリエーションでは、2038 年 1 月 18 日 23:59:59 (UTC) までの日付のみを表現できます。 これらの関数の日付範囲の下限は、いずれも 1970 年 1 月 1 日の午前 0 時です。

時間のサイズを明示的に指定するバージョンを使用する具体的な理由がない限り、 **_findfirst** または **_wfindfirst** を使用するか、3 GB を超えるファイルサイズをサポートする必要がある場合は **_findfirsti64** または **_wfindfirsti64** を使用します。 これらの関数はすべて 64 ビットの時刻型です。 以前のバージョンでは、これらの関数は 32 ビットの時刻型を使用していました。 これがアプリケーションの互換性に影響する変更である場合は、 **_USE_32BIT_TIME_T** を定義して、以前の動作に戻すことができます。 **_USE_32BIT_TIME_T** が定義されている場合、 **_findfirst**、 **_Finfirsti64**、および対応する Unicode バージョンは32ビット時刻を使用します。

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

### <a name="time-type-and-file-length-type-variations-of-_findfirst"></a>_findfirst の時刻型とファイル長型のバリエーション

|関数|**_USE_32BIT_TIME_T** 定義されていますか?|時刻型|ファイル長型|
|---------------|----------------------------------|---------------|----------------------|
|**_findfirst**、 **_wfindfirst**|未定義|64 ビット|32 ビット|
|**_findfirst**、 **_wfindfirst**|定義済み|32 ビット|32 ビット|
|**_findfirst32**、 **_wfindfirst32**|マクロ定義の影響を受けない|32 ビット|32 ビット|
|**_findfirst64**、 **_wfindfirst64**|マクロ定義の影響を受けない|64 ビット|64 ビット|
|**_findfirsti64**、 **_wfindfirsti64**|未定義|64 ビット|64 ビット|
|**_findfirsti64**、 **_wfindfirsti64**|定義済み|32 ビット|64 ビット|
|**_findfirst32i64**、 **_wfindfirst32i64**|マクロ定義の影響を受けない|32 ビット|64 ビット|
|**_findfirst64i32**、 **_wfindfirst64i32**|マクロ定義の影響を受けない|64 ビット|32 ビット|

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfindfirst**|**_findfirst**|**_findfirst**|**_wfindfirst**|
|**_tfindfirst32**|**_findfirst32**|**_findfirst32**|**_wfindfirst32**|
|**_tfindfirst64**|**_findfirst64**|**_findfirst64**|**_wfindfirst64**|
|**_tfindfirsti64**|**_findfirsti64**|**_findfirsti64**|**_wfindfirsti64**|
|**_tfindfirst32i64**|**_findfirst32i64**|**_findfirst32i64**|**_wfindfirst32i64**|
|**_tfindfirst64i32**|**_findfirst64i32**|**_findfirst64i32**|**_wfindfirst64i32**|

## <a name="requirements"></a>要件

|機能|必須ヘッダー|
|--------------|---------------------|
|**_findfirst**|\<io.h>|
|**_findfirst32**|\<io.h>|
|**_findfirst64**|\<io.h>|
|**_findfirsti64**|\<io.h>|
|**_findfirst32i64**|\<io.h>|
|**_findfirst64i32**|\<io.h>|
|**_wfindfirst**|\<io.h> または \<wchar.h>|
|**_wfindfirst32**|\<io.h> または \<wchar.h>|
|**_wfindfirst64**|\<io.h> または \<wchar.h>|
|**_wfindfirsti64**|\<io.h> または \<wchar.h>|
|**_wfindfirst32i64**|\<io.h> または \<wchar.h>|
|**_wfindfirst64i32**|\<io.h> または \<wchar.h>|

互換性について詳しくは、「 [Compatibility](../../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="see-also"></a>関連項目

[システムコール](../../c-runtime-library/system-calls.md)<br/>
[ファイル名検索関数](../../c-runtime-library/filename-search-functions.md)<br/>
