---
title: コンパイラ エラー C2277
ms.date: 11/04/2016
f1_keywords:
- C2277
helpviewer_keywords:
- C2277
ms.assetid: 15a83b07-8731-4524-810b-267f65a7844f
ms.openlocfilehash: 5b20594df8a250a54a0fd5902e0453f7438cbbfd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448088"
---
# <a name="compiler-error-c2277"></a>コンパイラ エラー C2277

'identifier': このメンバー関数のアドレスを取得することはできません

メンバー関数のアドレスを取得することはできません。

次の例では、C2277 が生成されます。

```
// C2277.cpp
class A {
public:
   A();
};
(*pctor)() = &A::A;   // C2277
```