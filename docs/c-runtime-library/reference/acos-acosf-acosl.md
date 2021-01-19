---
title: acos、acosf、acosl
description: Acos、acosf、acosl の API リファレンス浮動小数点値のアークコサインを計算する。
ms.date: 1/15/2021
api_name:
- acosf
- acos
- acosl
- _o_acos
- _o_acosf
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
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- acos
- acosl
- acosf
- math/acosf
- math/acosl
helpviewer_keywords:
- acos function
- acosl function
- acosf function
- trigonometric functions
- arccosine function
ms.openlocfilehash: 63a9c9577e252c506191b7a49ec9da6502968095
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2021
ms.locfileid: "98563836"
---
# <a name="acos-acosf-acosl"></a>`acos`, `acosf`, `acosl`

アークコサインを計算します。

## <a name="syntax"></a>構文

```C
double acos( double x );
float acosf( float x );
long double acosl( long double x );
#define acos(X) // Requires C11 or higher

float acos( float x );   // C++ only
long double acos( long double x );   // C++ only
```

### <a name="parameters"></a>パラメーター

*`x`*\
アークコサイン (逆余弦) を計算する-1 ~ 1 の範囲の値。

## <a name="return-value"></a>戻り値

関数は、 **`acos`** 0 ~ πラジアンの範囲の *x* のアークコサインを返します。

既定では、 *`x`* が-1 未満または1より大きい場合、は **`acos`** 不定を返します。

|入力|`SEH` 例外的|`Matherr` 例外的|
|-----------|-------------------|-----------------------|
|`± ∞`|`INVALID`|`_DOMAIN`|
|`± QNAN, IND`|なし|`_DOMAIN`|
|&#124;`x`&#124;>1|`INVALID`|`_DOMAIN`|

## <a name="remarks"></a>注釈

C++ ではオーバーロードが可能であるため、 **`acos`** 型と型を受け取って返すのオーバーロードを呼び出すことができ **`float`** **`long double`** ます。 C プログラムでは、 `<tgmath.h>` この関数を呼び出すためにマクロを使用している場合を除き、は **`acos`** 常にを受け取り、を返し **`double`** ます。

マクロを使用する場合 `<tgmath.h>` `acos()` 、引数の型によって、どのバージョンの関数が選択されているかが決まります。 詳細については [、「型汎用の算術演算](../../c-runtime-library/tgmath.md) 」を参照してください。

既定では、この関数のグローバル状態はアプリケーションにスコープが設定されています。 これを変更するには、「 [CRT でのグローバル状態](../global-state.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|省略可能なヘッダー|
|-------------|---------------------|----------------------|
|**`acos`**, **`acosf`**, **`acosl`**|`<math.h>`|`<errno.h>`|
|**`acos()`** マクロ | `<tgmath.h>` ||

## <a name="example"></a>例

このプログラムは、-1 ～ 1 の範囲の値の入力を求めます。 入力値がこの範囲外の場合、`_DOMAIN` エラー メッセージを生成します。 有効な値が入力された場合、プログラムはその値のアークサインとアークコサインを出力します。

```C
// crt_asincos.c
// arguments: 0

#include <math.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( int ac, char* av[] )
{
    double  x,
            y;
    errno_t err;

    // argument checking
    if (ac != 2)
    {
        fprintf_s( stderr, "Usage: %s <number between -1 and 1>\n",
                   av[0]);
        return 1;
    }

    // Convert argument into a double value
    if ((err = sscanf_s( av[1], "%lf", &x )) != 1)
    {
        fprintf_s( stderr, "Error converting argument into ",
                   "double value.\n");
        return 1;
    }

    // Arcsine of X
    y = asin( x );
    printf_s( "Arcsine of %f = %f\n", x, y );

    // Arccosine of X
    y = acos( x );
    printf_s( "Arccosine of %f = %f\n", x, y );
}
```

```Output
Arcsine of 0.000000 = 0.000000
Arccosine of 0.000000 = 1.570796
```

## <a name="see-also"></a>関連項目

[浮動小数点のサポート](../../c-runtime-library/floating-point-support.md)\
[`asin`, `asinf`, `asinl`](asin-asinf-asinl.md)\
[`atan`, `atanf`, `atanl`, `atan2`, `atan2f`, `atan2l`](atan-atanf-atanl-atan2-atan2f-atan2l.md)\
[`cos`, `cosf`, `cosl`](cos-cosf-cosl.md)\
[`_matherr`](matherr.md)\
[`sin`, `sinf`, `sinl`](sin-sinf-sinl.md)\
[`tan`, `tanf`, `tanl`](tan-tanf-tanl.md)