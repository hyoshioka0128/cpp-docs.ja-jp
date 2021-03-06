---
title: improper_lock クラス
ms.date: 11/04/2016
f1_keywords:
- improper_lock
- CONCRT/concurrency::improper_lock
- CONCRT/concurrency::improper_lock::improper_lock
helpviewer_keywords:
- improper_lock class
ms.assetid: 8f494942-7748-4a2a-8de2-23414bfe6346
ms.openlocfilehash: de7393c9186a1572040acd18854b5b3046b239f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552790"
---
# <a name="improperlock-class"></a>improper_lock クラス

このクラスは、ロックが正しく取得されなかった場合にスローされる例外を表します。

## <a name="syntax"></a>構文

```
class improper_lock : public std::exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[improper_lock](#ctor)|オーバーロードされます。 `improper_lock exception` を構築します。|

## <a name="remarks"></a>Remarks

通常、同じコンテキストで再帰的に再入不可能なロックの取得を試行したときにこの例外がスローされます。

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`improper_lock`

## <a name="requirements"></a>必要条件

**ヘッダー:** concrt.h

**名前空間:** concurrency

##  <a name="ctor"></a> improper_lock

`improper_lock exception` を構築します。

```
explicit _CRTIMP improper_lock(_In_z_ const char* _Message) throw();

improper_lock() throw();
```

### <a name="parameters"></a>パラメーター

*メッセージ (_m)*<br/>
エラーの説明メッセージ。

## <a name="see-also"></a>関連項目

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[critical_section クラス](critical-section-class.md)<br/>
[reader_writer_lock クラス](reader-writer-lock-class.md)
