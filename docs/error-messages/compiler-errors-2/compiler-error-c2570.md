---
title: コンパイラ エラー C2570
ms.date: 11/04/2016
f1_keywords:
- C2570
helpviewer_keywords:
- C2570
ms.assetid: d65d0b32-2fac-464a-bcdf-0ebcedf3bf32
ms.openlocfilehash: 447869b029df41219f71dcc633e9ae8a3934e0ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549579"
---
# <a name="compiler-error-c2570"></a>コンパイラ エラー C2570

'identifier': 共用体は基底クラスを含めることはできません

共用体は、クラス、構造体または共用体から派生します。 これは認められていません。 代わりに、クラスまたは構造体として、派生型を宣言します。

次の例では、C2570 が生成されます。

```
// C2570.cpp
// compile with: /c
class base {};
union hasPubBase : public base {};   // C2570
union hasNoBase {};   // OK
```