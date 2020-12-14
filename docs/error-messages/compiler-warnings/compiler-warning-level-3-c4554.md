---
description: '詳細情報: コンパイラの警告 (レベル 3) C4554'
title: コンパイラの警告 (レベル 3) C4554
ms.date: 11/04/2016
f1_keywords:
- C4554
helpviewer_keywords:
- C4554
ms.assetid: 55bb68f0-2e80-4330-8921-51083c4f8d53
ms.openlocfilehash: daed8757cca5c9d9286f6f6bf94c55149c1687c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257837"
---
# <a name="compiler-warning-level-3-c4554"></a>コンパイラの警告 (レベル 3) C4554

' operator ': 演算子の優先順位に誤りがあることを確認してください。かっこを使用して優先順位を明確にする

次の例では、C4554 が生成されます。

```cpp
// C4554.cpp
// compile with: /W3 /WX
int main() {
   int a = 0, b = 0, c = 0;
   a = a << b + c;   // C4554
   // probably intended (a << b) + c,
   // but will get a << (b + c)
}
```
