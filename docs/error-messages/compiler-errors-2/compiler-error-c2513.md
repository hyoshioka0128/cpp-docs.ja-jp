---
title: コンパイラ エラー C2513
ms.date: 11/04/2016
f1_keywords:
- C2513
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
ms.openlocfilehash: 13840246a5dc6a1c1bdbcb55dc47f212ee353d81
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561202"
---
# <a name="compiler-error-c2513"></a>コンパイラ エラー C2513

'type': '=' の前に変数が宣言されていません。

識別子のない変数宣言で型指定子が表示されます。

次の例では、C2513 が生成されます。

```
// C2513.cpp
int main() {
   int = 9;   // C2513
   int i = 9;   // OK
}
```

このエラーは、Visual Studio .NET 2003 のコンパイラ準拠作業の結果として生成することもできます。 使用できなくなった typedef の初期化。 Typedef の初期化では、標準では許可されていませんし、今すぐ、コンパイラ エラーを生成します。

```
// C2513b.cpp
// compile with: /c
typedef struct S {
   int m_i;
} S = { 1 };   // C2513
// try the following line instead
// } S;
```

削除する方法もあります。`typedef`集計初期化子リストが、これで変数を定義するは、型と同じ名前で変数を作成し、型名を非表示にするため、推奨されません。