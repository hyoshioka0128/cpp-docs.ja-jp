---
title: 既定の名前空間
ms.date: 12/30/2016
ms.assetid: 4712e9dc-57ba-43cc-811e-022e1dae4de8
ms.openlocfilehash: ffea9e1132b4c66f38661392cbafb94635b318e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558721"
---
# <a name="default-namespace"></a>既定の名前空間

`default`名前空間のスコープと C + でサポートされている組み込み型/cli CX します。

## <a name="syntax"></a>構文

```
namespace default;
```

### <a name="members"></a>メンバー

組み込み型はすべて、次のメンバーを継承します。

|||
|-|-|
|[default::(type_name)::Equals](../cppcx/default-type-name-equals-method.md)|指定したオブジェクトが、現在のオブジェクトと等しいかどうかを判断します。|
|[default::(type_name)::GetHashCode](../cppcx/default-type-name-gethashcode-method.md)|このインスタンスのハッシュ コードを返します。|
|[default::(type_name)::GetType](../cppcx/default-type-name-gettype-method.md)|現在の型を表す文字列を返します。|
|[default::(type_name)::ToString](../cppcx/default-type-name-tostring-method.md)|現在の型を表す文字列を返します。|

### <a name="built-in-types"></a>組み込み型

|名前|説明|
|----------|-----------------|
|`char16`|Unicode (UTF-16) コード ポイントを表す 16 ビットの数字以外の値。|
|`float32`|32 ビットの IEEE 754 浮動小数点数。|
|`float64`|64 ビットの IEEE 754 浮動小数点数。|
|`int16`|16 ビット符号付き整数。|
|`int32`|32 ビット符号付き整数。|
|`int64`|64 ビット符号付き整数。|
|`int8`|8 ビット符号付き数値。|
|`uint16`|16 ビット符号なし整数。|
|`uint32`|32 ビット符号なし整数|
|`uint64`|64 ビット符号なし整数。|
|`uint8`|8 ビット符号なし数値。|

### <a name="requirements"></a>必要条件

**ヘッダー:** vccorlib.h

## <a name="see-also"></a>関連項目

[Visual C 言語リファレンス](../cppcx/visual-c-language-reference-c-cx.md)