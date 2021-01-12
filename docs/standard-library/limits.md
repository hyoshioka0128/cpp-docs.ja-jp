---
description: '詳細情報: &lt; 制限&gt;'
title: '&lt;limits&gt;'
ms.date: 11/04/2016
f1_keywords:
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: 23601b4b7f7ea06071a6b1f5fbd87ce0a0babce3
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126391"
---
# <a name="ltlimitsgt"></a>&lt;limits&gt;

クラステンプレートと、 `numeric_limits` 浮動小数点の表現と丸め処理に関する2つの列挙体を定義します。

## <a name="requirements"></a>必要条件

**ヘッダー:**\<limits>

**名前空間:** std

## <a name="remarks"></a>解説

クラスの明示的な特殊化には、 `numeric_limits` 文字、整数、浮動小数点型など、基本型の多くのプロパティが記述さ **`bool`** れています。これは、C++ 言語の規則ではなく、定義された実装です。 「」で説明されているプロパティに \<limits> は、精度、最小および最大サイズの表現、丸め、およびシグナリングの種類のエラーが含まれます。

## <a name="members"></a>メンバー

### <a name="enumerations"></a>列挙型

|名前|説明|
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|この列挙体では、小さすぎて、正規化された値としては表現できない非正規化された浮動小数点値を表現するために、実装で選択できるさまざまなメソッドを記述します。|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|この列挙体では、浮動小数点値を整数値に丸めるために、実装で選択できるさまざまなメソッドを記述します。|

### <a name="classes"></a>クラス

|名前|説明|
|-|-|
|[numeric_limits クラス](../standard-library/numeric-limits-class.md)|クラステンプレートでは、組み込みの数値型の算術プロパティについて説明します。|

## <a name="see-also"></a>関連項目

[ヘッダーファイルのリファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリのスレッドセーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
