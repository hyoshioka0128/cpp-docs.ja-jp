---
description: '詳細情報: &lt; 将来の &gt; 列挙型'
title: '&lt;future&gt; 列挙型'
ms.date: 11/04/2016
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
ms.openlocfilehash: 473533d5d22ac5708af7a86cc58a57ac033545af
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97232136"
---
# <a name="ltfuturegt-enums"></a>&lt;future&gt; 列挙型

[future_errc](#future_errc)\
[future_status](#future_status)\
[起動する](#launch)

## <a name="future_errc-enumeration"></a><a name="future_errc"></a> future_errc 列挙型

[future_error](../standard-library/future-error-class.md) クラスによって報告されるすべてのエラーのシンボル名を提供します。

```cpp
class future_errc {
   broken_promise,
   future_already_retrieved,
   promise_already_satisfied,
   no_state
   };
```

## <a name="future_status-enumeration"></a><a name="future_status"></a> future_status 列挙型

期限が設定された wait 関数から返される理由のシンボル名を提供します。

```cpp
enum future_status{
    ready,
    timeout,
    deferred
};
```

## <a name="launch-enumeration"></a><a name="launch"></a> 起動列挙型

テンプレート関数 [async](../standard-library/future-functions.md#async) で使用できるモードを示すビットマスク型を表します。

```cpp
class launch{
   async,
   deferred
   };
```

## <a name="see-also"></a>関連項目

[\<future>](../standard-library/future.md)
