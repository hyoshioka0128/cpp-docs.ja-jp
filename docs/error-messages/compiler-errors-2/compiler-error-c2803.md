---
description: 詳細については、「コンパイラエラー C2803」を参照してください。
title: コンパイラ エラー C2803
ms.date: 11/04/2016
f1_keywords:
- C2803
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
ms.openlocfilehash: 405c14d05bad4c505d847b8ab2648a7ace3b9a4b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297435"
---
# <a name="compiler-error-c2803"></a>コンパイラ エラー C2803

' operator operator ' には、クラス型の仮引数が少なくとも1つ必要です

オーバーロードされた演算子にクラス型のパラメーターがありません。

参照によってパラメーターを1つ以上渡す必要があります (ポインターを使用しないでください)。または、値によって "a < b" (a と b が型クラス A である) を書き込むことができます。

両方のパラメーターがポインターである場合は、ポインターアドレスの純粋な比較であり、ユーザー定義の変換は使用されません。

次の例では、C2803 が生成されます。

```cpp
// C2803.cpp
// compile with: /c
class A{};
bool operator< (const A *left, const A *right);   // C2803
// try the following line instead
// bool operator< (const A& left, const A& right);
```
