---
title: コンパイラ エラー C3804
ms.date: 11/04/2016
f1_keywords:
- C3804
helpviewer_keywords:
- C3804
ms.assetid: 7c4cda28-ec96-4d04-937b-36dbd9944722
ms.openlocfilehash: e83380696aca3d6d45c235925b830bef9e3061a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544587"
---
# <a name="compiler-error-c3804"></a>コンパイラ エラー C3804

'property_accessor': アクセサー メソッドをプロパティには、いずれかが必要がありますはすべて静的、またはすべてスタティックでないです。

アクセサー関数が静的にできる非 trivial プロパティを定義するときにインスタンスが両方のか。

詳細については、「 [property](../../windows/property-cpp-component-extensions.md) 」を参照してください。

## <a name="example"></a>例

次の例では、C3804 が生成されます。

```
// C3804.cpp
// compile with: /c /clr
ref struct A {

   property int i {
      static int get() {}
      void set(int i) {}
   }   // C3804 error

   // OK
   property int j {
      int get() { return 0; }
      void set(int i) {}
   }

   property int k {
      static int get() { return 0; }
      static void set(int i) {}
   }
};
```