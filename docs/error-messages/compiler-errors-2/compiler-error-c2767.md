---
description: 詳細については、「コンパイラエラー C2767」を参照してください。
title: コンパイラエラー C2767
ms.date: 11/04/2016
f1_keywords:
- C2767
helpviewer_keywords:
- C2767
ms.assetid: e8f84178-a160-4d71-a236-07e4fcc11e96
ms.openlocfilehash: 4acd75d1b7782a7eb694e7b91fc19cac45a6319e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239481"
---
# <a name="compiler-error-c2767"></a>コンパイラエラー C2767

マネージまたは WinRTarray の次元の不一致: 予期された N 個の引数が必要です。

マネージド配列または WinRT 配列の宣言の形式が正しくありません。 詳細については、「 [配列](../../extensions/arrays-cpp-component-extensions.md)」を参照してください。

次の例では、C2767 を生成し、その修正方法を示しています。

```cpp
// C2767.cpp
// compile with: /clr
int main() {
   array<int> ^p1 = new array<int>(2,3); // C2767
   array<int> ^p2 = new array<int>(2);   // OK
}
```
