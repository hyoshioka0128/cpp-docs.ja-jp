---
title: コンパイラ エラー C3708
ms.date: 11/04/2016
f1_keywords:
- C3708
helpviewer_keywords:
- C3708
ms.assetid: 45e71564-9c7f-437f-98d8-a735ce162ed0
ms.openlocfilehash: 7ee9d59f12cc9e748b08b3e4a704420ea5c58be6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661891"
---
# <a name="compiler-error-c3708"></a>コンパイラ エラー C3708

'interface': 'keyword'; の不適切な使用互換性のあるイベント ソースのメンバーである必要があります。

イベントとしてインターフェイスを宣言するには、イベントの宣言は、イベント ソースでなければなりません。

次の例では、C3708 が生成されます。

```
// C3708.cpp
// compile with: /c
#define _ATL_ATTRIBUTES 1
#include "atlbase.h"
#include "atlcom.h"

[ module(name="MyLibrary")];

[ object, uuid("00000000-0000-0000-0000-000000000001") ]
__interface I {
   HRESULT func();
};

[ object, uuid("00000000-0000-0000-0000-000000000002") ]
__interface II {
   HRESULT func();
};

__event __interface I;   // C3708

// put the event in an event source
[ coclass, event_source(com), uuid("00000000-0000-0000-0000-000000000003") ]
struct E : II {
   __event __interface II;
};
```