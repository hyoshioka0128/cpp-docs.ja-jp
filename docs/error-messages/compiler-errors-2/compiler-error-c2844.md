---
description: 詳細については、「コンパイラエラー C2844」を参照してください。
title: コンパイラ エラー C2844
ms.date: 11/04/2016
f1_keywords:
- C2844
helpviewer_keywords:
- C2844
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
ms.openlocfilehash: 030d8526e7bfd85e7bcca1c115f1b5ce5d45c3aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97260280"
---
# <a name="compiler-error-c2844"></a>コンパイラ エラー C2844

' member ': インターフェイス ' interface ' のメンバーにすることはできません

[インターフェイスクラス](../../extensions/interface-class-cpp-component-extensions.md)は、プロパティでもない限り、データメンバーを含むことはできません。

プロパティまたはメンバー関数以外のものは、インターフェイスでは使用できません。 さらに、コンストラクター、デストラクター、および演算子は使用できません。

次の例では、C2844 が生成されます。

```cpp
// C2844a.cpp
// compile with: /clr /c
public interface class IFace {
   int i;   // C2844
   // try the following line instead
   // property int Size;
};
```
