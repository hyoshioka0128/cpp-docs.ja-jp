---
title: コンパイラ エラー C3395
ms.date: 11/04/2016
f1_keywords:
- C3395
helpviewer_keywords:
- C3395
ms.assetid: 26a9ebc9-ed97-47ce-b436-19aa2bcf6e50
ms.openlocfilehash: 2e5234abcbe46e17035fd0b16e9816c879d86cfe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604120"
---
# <a name="compiler-error-c3395"></a>コンパイラ エラー C3395

'function': 方式を伴う関数に適用できません、 \__clrcall 呼び出し規約

`__declspec(dllexport)` [_ _clrcall](../../cpp/clrcall.md)は互換性がありません。  詳細については、次を参照してください。 [dllexport、dllimport](../../cpp/dllexport-dllimport.md)します。

次の例では、C3395 が生成されます。

```
// C3395.cpp
// compile with: /clr /c

__declspec(dllexport) void __clrcall Test(){}   // C3395
void __clrcall Test2(){}   // OK
__declspec(dllexport) void Test3(){}   // OK
```