---
title: abort の使用
ms.date: 11/04/2016
f1_keywords:
- Abort
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
ms.openlocfilehash: 0961f6f88f5de4d435fa65e50b9dbdbc478e7608
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591829"
---
# <a name="using-abort"></a>abort の使用

呼び出す、[中止](../c-runtime-library/reference/abort.md)関数によっては直ちに終了します。 初期化されたグローバルな静的オブジェクトの通常のデストラクション処理は実行されません。 また、`atexit` 関数を使用して指定されている特殊な処理も実行されません。

## <a name="see-also"></a>関連項目

[終了に関するその他の考慮事項](../cpp/additional-termination-considerations.md)