---
title: コンパイラ エラー C2107
ms.date: 11/04/2016
f1_keywords:
- C2107
helpviewer_keywords:
- C2107
ms.assetid: 2866a121-884e-4bb5-8613-36de5817000e
ms.openlocfilehash: 2b388495c6ce31452bd3f8e8bfc6c26a6bfbdbe8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643028"
---
# <a name="compiler-error-c2107"></a>コンパイラ エラー C2107

無効なインデックスです、間接参照は許可されていません

ポインターではない式に添字が使われています。

## <a name="example"></a>例

値型の `this` ポインターを不正に使用して型の既定のインデクサーにアクセスすると、C2107 エラーが発生します。 詳細については、次を参照してください。[セマンティクスは、このポインター](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer)します。

次の例では、c2107 エラーが生成されます。

```
// C2107.cpp
// compile with: /clr
using namespace System;

value struct B {
   property String ^ default[String ^] {
      String ^ get(String ^ data) {
         return "abc";
      }
   }
   void Test() {
      Console::WriteLine("{0}", this["aa"]);   // C2107
      Console::WriteLine("{0}", this->default["aa"]);   // OK
   }
};

int main() {
   B ^ myb = gcnew B();
   myb->Test();
}
```