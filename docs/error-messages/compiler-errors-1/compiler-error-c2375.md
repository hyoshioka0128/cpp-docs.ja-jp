---
title: コンパイラ エラー C2375
ms.date: 11/04/2016
f1_keywords:
- C2375
helpviewer_keywords:
- C2375
ms.assetid: 193c5e8b-1b20-4928-8a02-8c1cddaf2a26
ms.openlocfilehash: 162f1b13ea76a92db6fbef08124a1e46bc4e18a7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452105"
---
# <a name="compiler-error-c2375"></a>コンパイラ エラー C2375

'function' : 再定義されています。異なるリンケージです

関数は、別のリンケージ指定子で既に宣言されています。

次の例では C2375 が生成されます。

```
// C2375.cpp
// compile with: /Za /c
extern void func( void );
static void func( void );   // C2375
static void func2( void );   // OK
```