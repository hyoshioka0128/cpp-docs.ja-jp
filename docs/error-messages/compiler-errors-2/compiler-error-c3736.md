---
description: 詳細については、「コンパイラエラー C3736」を参照してください。
title: コンパイラ エラー C3736
ms.date: 11/04/2016
f1_keywords:
- C3736
helpviewer_keywords:
- C3736
ms.assetid: 579b773c-41e7-40ea-8382-2e3ce2667f4c
ms.openlocfilehash: 6ec22012efb9de3ec7f0b8911ed45f4f6a724135
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244993"
---
# <a name="compiler-error-c3736"></a>コンパイラ エラー C3736

' event ': メソッドであるか、マネージイベントの場合はデータメンバーである必要があります。

ネイティブイベントと COM イベントは、メソッドである必要があります。 .NET イベントはデータメンバーでもかまいません。

次の例では、C3736 が生成されます。

```cpp
// C3736.cpp
struct A {
   __event int e();
};

struct B {
   int f;   // C3736
   // The following line resolves the error.
   // int f();
   B(A* a) {
      __hook(&A::e, a, &B::f);
   }
};

int main() {
}
```
