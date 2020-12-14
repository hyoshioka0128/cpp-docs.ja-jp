---
description: '詳細情報: コンパイラの警告 (レベル 1) C4807'
title: コンパイラの警告 (レベル 1) C4807
ms.date: 11/04/2016
f1_keywords:
- C4807
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
ms.openlocfilehash: 4c015d2ee7c566199411374402719c4a8eaee37f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97238142"
---
# <a name="compiler-warning-level-1-c4807"></a>コンパイラの警告 (レベル 1) C4807

'operation': 'type' 型と 'type' 型の符号付きビットフィールドの混用は安全ではありません。

この警告は、1ビットの符号付きビットフィールドと変数を比較したときに生成され **`bool`** ます。 1ビットの符号付きビットフィールドには、値-1 または0のみを含めることができるため、と比較するのは危険です **`bool`** 。 はと同じであり、 **`bool`** **`bool`** 0 または1のみを保持できるため、混合と1ビットの符号なしビットフィールドに関する警告は生成されません。

## <a name="example"></a>例

次の例では C4807 が生成されます。

```cpp
// C4807.cpp
// compile with: /W1
typedef struct bitfield {
   signed mybit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bool b = true;

   // try..
   // int b = true;

   bf.mybit = -1;
   if (b == bf.mybit) {   // C4807
      b = false;
   }
}
```
