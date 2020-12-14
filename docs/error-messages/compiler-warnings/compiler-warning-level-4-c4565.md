---
description: '詳細情報: コンパイラの警告 (レベル 4) C4565'
title: コンパイラの警告 (レベル 4) C4565
ms.date: 08/27/2018
f1_keywords:
- C4565
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
ms.openlocfilehash: bdcf36234ef5a7d8f371d8d25d31b9cb3a36590d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255146"
---
# <a name="compiler-warning-level-4-c4565"></a>コンパイラの警告 (レベル 4) C4565

> '*function*': 再定義します。シンボルは、以前に __declspec (*修飾子*) を使用して宣言されていました。

## <a name="remarks"></a>解説

シンボルが再定義または再宣言されましたが、最初の定義または宣言とは異なり、2番目の定義または宣言に **`__declspec`** 修飾子 (*修飾子*) がありませんでした。 これは、情報提供の警告です。 この警告を修正するには、定義の1つを削除します。

## <a name="example"></a>例

次の例では、C4565 が生成されます。

```cpp
// C4565.cpp
// compile with: /W4 /LD
__declspec(noalias) void f();
void f();   // C4565
```
