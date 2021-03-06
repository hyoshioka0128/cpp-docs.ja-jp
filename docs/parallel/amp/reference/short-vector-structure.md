---
title: short_vector 構造体
ms.date: 11/04/2016
f1_keywords:
- short_vector
- AMP_SHORT_VECTORS/short_vector
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector::short_vector Constructor
ms.assetid: e4f50b8f-1150-437d-b58c-79c5fb883708
ms.openlocfilehash: 535aeee1ea52ae6b248220d9330cd1d2235a99a4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594052"
---
# <a name="shortvector-structure"></a>short_vector 構造体

short_vector は short ベクターを汎用的にプログラミングに役立つメタプログラミングの定義を提供します。

## <a name="syntax"></a>構文

```
template<
    typename _Scalar_type,
    int _Size
>
struct short_vector;
template<>
struct short_vector<unsigned int, 1>;
template<>
struct short_vector<unsigned int, 2>;
template<>
struct short_vector<unsigned int, 3>;
template<>
struct short_vector<unsigned int, 4>;
template<>
struct short_vector<int, 1>;
template<>
struct short_vector<int, 2>;
template<>
struct short_vector<int, 3>;
template<>
struct short_vector<int, 4>;
template<>
struct short_vector<float, 1>;
template<>
struct short_vector<float, 2>;
template<>
struct short_vector<float, 3>;
template<>
struct short_vector<float, 4>;
template<>
struct short_vector<unorm, 1>;
template<>
struct short_vector<unorm, 2>;
template<>
struct short_vector<unorm, 3>;
template<>
struct short_vector<unorm, 4>;
template<>
struct short_vector<norm, 1>;
template<>
struct short_vector<norm, 2>;
template<>
struct short_vector<norm, 3>;
template<>
struct short_vector<norm, 4>;
template<>
struct short_vector<double, 1>;
template<>
struct short_vector<double, 2>;
template<>
struct short_vector<double, 3>;
template<>
struct short_vector<double, 4>;
```

#### <a name="parameters"></a>パラメーター

*_Scalar_type*<br/>

*サイズ) (_s*<br/>

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|`type`||

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[short_vector::short_vector コンス トラクター](#ctor)||

## <a name="inheritance-hierarchy"></a>継承階層

`short_vector`

## <a name="requirements"></a>必要条件

**ヘッダー:** amp_short_vectors.h

**Namespace:** concurrency::graphics

##  <a name="ctor"></a>  short_vector::short_vector コンス トラクター

```
short_vector();
```

## <a name="see-also"></a>関連項目

[Concurrency::graphics 名前空間](concurrency-graphics-namespace.md)
