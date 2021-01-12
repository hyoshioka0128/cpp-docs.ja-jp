---
description: '詳細については、次を参照してください: &lt; hash_map&gt;'
title: '&lt;hash_map&gt;'
ms.date: 01/18/2018
f1_keywords:
- <hash_map>
helpviewer_keywords:
- hash_map header
ms.openlocfilehash: 9d8274958a0f6b89892ec2c1c70080cd090d1c03
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2021
ms.locfileid: "98125975"
---
# <a name="lthash_mapgt"></a>&lt;hash_map&gt;

> [!NOTE]
> このヘッダーは廃止され、互換性のために残されています。 代替手段は [\<unordered_map>](unordered-map.md) です。

コンテナークラステンプレート hash_map と hash_multimap と、そのサポートテンプレートを定義します。

## <a name="syntax"></a>構文

```cpp
#include <hash_map>
```

### <a name="operators"></a>オペレーター

|hash_map バージョン|hash_multimap バージョン|説明|
|-----------------------|----------------------------|-----------------|
|[operator!= (hash_map)](hash-map-operators.md#op_neq)|[operator! = (hash_multimap)](hash-map-operators.md#op_neq_mm)|演算子の左側の hash_map または hash_multimap オブジェクトが右側の hash_map または hash_multimap オブジェクトと等しくないかどうかをテストします。|
|[operator = = (hash_map)](hash-map-operators.md#op_eq_eq)|[operator== (hash_multimap)](hash-map-operators.md#op_eq_eq_mm)|演算子の左側の hash_map または hash_multimap オブジェクトが右側の hash_map または hash_multimap オブジェクトと等しいかどうかをテストします。|

### <a name="specialized-template-functions"></a>特殊テンプレート関数

|hash_map バージョン|hash_multimap バージョン|説明|
|-----------------------|----------------------------|-----------------|
|[swap (hash_map)](hash-map-class.md#swap)|[swap (hash_multimap)](hash-multimap-class.md#swap)|2 つの hash_map または hash_multimap の要素を交換します。|

### <a name="classes"></a>クラス

|クラス|説明|
|-|-|
|[hash_compare クラス](hash-compare-class.md)|ハッシュ連想コンテナー (hash_map、hash_multimap、hash_set、または hash_multiset) のいずれかで使用できるオブジェクトを、そのオブジェクトに `Traits` 含まれる要素の順序付けおよびハッシュを行う既定のパラメーターオブジェクトとして記述します。|
|[value_compare クラス](value-compare-class.md)|要素のキーの値を比較し、要素の hash_map 内の相対順序を決定して、hash_map の要素を比較できる関数オブジェクトを提供します。|
|[hash_map クラス](hash-map-class.md)|一意の並べ替えキーとそれに関連付けられている値のペアを要素として持つコレクションのデータを格納したり、迅速に取得したりするために使用されます。|
|[hash_multimap クラス](hash-multimap-class.md)|必ずしも一意ではない並べ替えキーとそれに関連付けられている値のペアを要素として持つコレクションのデータを格納したり、迅速に取得したりするために使用されます。|

## <a name="requirements"></a>必要条件

**ヘッダー:**\<hash_map>

**名前空間:** stdext

## <a name="see-also"></a>関連項目

[ヘッダーファイルのリファレンス](cpp-standard-library-header-files.md)\
[C++ 標準ライブラリのスレッドセーフ](thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリリファレンス](cpp-standard-library-reference.md)
