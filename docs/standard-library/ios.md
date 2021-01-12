---
description: '詳細情報: &lt; ios&gt;'
title: '&lt;ios&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ios>
helpviewer_keywords:
- ios header
ms.assetid: d3d4c161-2f37-4f04-93cc-0a2a89984a9c
ms.openlocfilehash: 9904c91c46eb34bc278a0ce877e157f01a6f9a26
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126040"
---
# <a name="ltiosgt"></a>&lt;ios&gt;

iostream 操作の基礎となる型と関数を定義します。 このヘッダーは通常、別の iostream ヘッダーによってインクルードされており、ユーザーが直接インクルードすることはほとんどありません。

## <a name="requirements"></a>必要条件

**ヘッダー**: \<ios>

**名前空間:** std

> [!NOTE]
> ライブラリは、 \<ios> ステートメントを使用し `#include <iosfwd>` ます。

## <a name="remarks"></a>解説

マニピュレーターとは、多種類の関数のグループです。 で宣言されたマニピュレーターは、 \<ios> [ios_base](../standard-library/ios-base-class.md)クラスの引数オブジェクトに格納されている値を変更します。 他のマニピュレーターは、このクラスから派生した型のオブジェクトによって制御されるストリームに対して操作を実行します。たとえば、 [basic_istream](../standard-library/basic-istream-class.md) または [basic_ostream](../standard-library/basic-ostream-class.md)のクラステンプレートの1つを特殊化します。 たとえば、 [noskipws](../standard-library/ios-functions.md#noskipws)(**str**) は、オブジェクトの format フラグをクリアし `ios_base::skipws` `str` ます。これは、次のいずれかの型になります。

マニピュレーターは、出力ストリームに挿入したり、入力ストリームから抽出したりすることでも呼び出すことができます。これは、`ios_base` から派生したクラスに特殊な挿入演算子と抽出演算子が指定されるためです。 例:

```cpp
istr>> noskipws;
```

[noskipws](../standard-library/ios-functions.md#noskipws)(**istr**) を呼び出します。

## <a name="members"></a>メンバー

### <a name="typedefs"></a>Typedefs

|名前|説明|
|-|-|
|[ios](../standard-library/ios-typedefs.md#ios)|従来の iostream ライブラリの ios クラスをサポートします。|
|[streamoff](../standard-library/ios-typedefs.md#streamoff)|内部操作をサポートします。|
|[streampos](../standard-library/ios-typedefs.md#streampos)|バッファー ポインターまたはファイル ポインターの現在の位置を保持します。|
|[streamsize](../standard-library/ios-typedefs.md#streamsize)|ストリームのサイズを指定します。|
|[wios](../standard-library/ios-typedefs.md#wios)|従来の iostream ライブラリの wios クラスをサポートします。|
|[wstreampos](../standard-library/ios-typedefs.md#wstreampos)|バッファー ポインターまたはファイル ポインターの現在の位置を保持します。|

### <a name="manipulators"></a>マニピュレーター

|名前|説明|
|-|-|
|[boolalpha](../standard-library/ios-functions.md#boolalpha)|[Bool](../cpp/bool-cpp.md)型の変数を **`true`** ストリームでまたはとして表示するように指定し **`false`** ます。|
|[alpha](../standard-library/ios-functions.md#dec)|整数変数を 10 進表記で表示するように指定します。|
|[defaultfloat](../standard-library/ios-functions.md#ios_defaultfloat)|浮動小数値に既定の表示形式を使用するように、`ios_base` オブジェクトのフラグを構成します。|
|[fixed](../standard-library/ios-functions.md#fixed)|浮動小数点数を固定 10 進表記で表示するように指定します。|
|[hex](../standard-library/ios-functions.md#hex)|整数変数を 16 進表記で表示するように指定します。|
|[hexfloat](../standard-library/ios-functions.md#hexfloat)|
|[internal](../standard-library/ios-functions.md#internal)|数値の符号を左揃え、数値を右揃えにします。|
|[左側](../standard-library/ios-functions.md#left)|出力幅に満たないテキストをストリーム フラッシュで左揃えに表示します。|
|[noboolalpha](../standard-library/ios-functions.md#noboolalpha)|[bool](../cpp/bool-cpp.md) 型の変数をストリームで 1 または 0 として表示するように指定します。|
|[noshowbase](../standard-library/ios-functions.md#noshowbase)|指定している数値表記の基底の設定をオフにします。|
|[noshowpoint](../standard-library/ios-functions.md#noshowpoint)|小数部分が 0 の浮動小数点数の整数部分のみを表示します。|
|[noshowpos](../standard-library/ios-functions.md#noshowpos)|正の数値に明示的に符号を付けないようにします。|
|[noskipws](../standard-library/ios-functions.md#noskipws)|入力ストリームで空白を読み取るようにします。|
|[nounitbuf](../standard-library/ios-functions.md#nounitbuf)|出力をバッファーし、バッファーが一杯になると、出力を処理します。|
|[nouppercase](../standard-library/ios-functions.md#nouppercase)|16 進数と指数表記の指数を小文字で表示します。|
|[シンガポール](../standard-library/ios-functions.md#oct)|整数変数を 8 進表記で表示するように指定します。|
|[right](../standard-library/ios-functions.md#right)|出力幅に満たないテキストをストリーム フラッシュで右揃えに表示します。|
|[学術](../standard-library/ios-functions.md#scientific)|浮動小数点数値を指数表記を使用して表示します。|
|[showbase](../standard-library/ios-functions.md#showbase)|数値表記の基底を指定します。|
|[showpoint](../standard-library/ios-functions.md#showpoint)|小数部分が 0 のときも浮動小数点数の整数部分と小数点の右側にある数字を表示します。|
|[showpos](../standard-library/ios-functions.md#showpos)|正の数値に明示的に符号を付けます。|
|[skipws](../standard-library/ios-functions.md#skipws)|入力ストリームで空白を読み飛ばします。|
|[unitbuf](../standard-library/ios-functions.md#unitbuf)|バッファーが空ではないときに、出力を処理します。|
|[uppercase](../standard-library/ios-functions.md#uppercase)|16 進数と指数表記の指数を大文字で表示します。|

### <a name="error-reporting"></a>[エラー報告]

|名前|説明|
|-|-|
|[io_errc](../standard-library/ios-functions.md#io_errc)||
|[is_error_code_enum](../standard-library/ios-functions.md#is_error_code_enum)||
|[iostream_category](../standard-library/ios-functions.md#iostream_category)||
|[make_error_code](../standard-library/ios-functions.md#make_error_code)||
|[make_error_condition](../standard-library/ios-functions.md#make_error_condition)||

### <a name="classes"></a>クラス

|名前|説明|
|-|-|
|[basic_ios](../standard-library/basic-ios-class.md)|クラステンプレートは、テンプレートパラメーターに依存する入力ストリーム (クラステンプレート [basic_istream](../standard-library/basic-istream-class.md)の) と出力ストリーム (クラステンプレート [basic_ostream](../standard-library/basic-ostream-class.md)) の両方に共通するストレージおよびメンバー関数を記述します。|
|[fpos](../standard-library/fpos-class.md)|クラステンプレートは、任意のストリーム内の任意のファイル位置インジケーターを復元するために必要なすべての情報を格納できるオブジェクトを表します。|
|[ios_base](../standard-library/ios-base-class.md)|このクラスは、テンプレート パラメーターに依存しない、入力ストリームと出力ストリームの両方に共通のストレージとメンバー関数を表します。|

## <a name="see-also"></a>関連項目

[ヘッダーファイルのリファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリのスレッドセーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream プログラミング](../standard-library/iostream-programming.md)\
[iostreams の規則](../standard-library/iostreams-conventions.md)
