---
title: コンパイラの警告 (レベル 4) C4690
ms.date: 07/03/2018
f1_keywords:
- C4690
helpviewer_keywords:
- C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
ms.openlocfilehash: c7facdde54b44ba2ce07db0447b251d7014f76c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518483"
---
# <a name="compiler-warning-level-4-c4690"></a>コンパイラの警告 (レベル 4) C4690

> \[ emitidl (pop)]: ポップがプッシュ

## <a name="remarks"></a>Remarks

[emitidl](../../windows/emitidl.md) 属性は、プッシュよりも 1 回多くポップされています。

## <a name="example"></a>例

次の例では C4690 警告が生成されます。 この問題を解決するには、レバーが回数とまったく同じ属性がポップされますを確認します。

```cpp
// C4690.cpp
// compile with: /c /W4
[emitidl(pop)];   // C4690
class x {};
```
