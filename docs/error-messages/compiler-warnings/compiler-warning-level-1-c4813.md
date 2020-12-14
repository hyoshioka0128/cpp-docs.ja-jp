---
description: '詳細情報: コンパイラの警告 (レベル 1) C4813'
title: コンパイラの警告 (レベル 1) C4813
ms.date: 11/04/2016
f1_keywords:
- C4813
helpviewer_keywords:
- C4813
ms.assetid: c30bf877-ab04-4fe4-897e-8162092426f0
ms.openlocfilehash: 01c240df7bf9abbee9a9971ec403ff1f3accb1ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255211"
---
# <a name="compiler-warning-level-1-c4813"></a>コンパイラの警告 (レベル 1) C4813

'function' : ローカル クラスの friend 関数が宣言されていません。

内部クラスの friend 関数が外側クラスで宣言されていませんでした。

次の例では C4813 が生成されます。

```cpp
// C4813.cpp
// compile with: /W1 /LD
void MyClass()
{
   // void func();
   class InnerClass
   {
      friend void func();   // C4813 uncomment declaration above
   };
}
```
