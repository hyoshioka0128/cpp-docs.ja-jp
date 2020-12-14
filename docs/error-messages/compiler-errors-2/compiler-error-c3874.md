---
description: 詳細については、「コンパイラエラー C3874」を参照してください。
title: コンパイラ エラー C3874
ms.date: 11/04/2016
f1_keywords:
- C3874
helpviewer_keywords:
- C3874
ms.assetid: fd55fc05-69a7-4237-b3b7-dca1d5400b4f
ms.openlocfilehash: c9e0b498d5daf5066c0e224c99dc6af47d689adc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97274568"
---
# <a name="compiler-error-c3874"></a>コンパイラ エラー C3874

' function ' の戻り値の型は ' type ' ではなく ' int ' でなければなりません

関数には、コンパイラによって予期された戻り値の型がありません。

次の例では、C3874 が生成されます。

```cpp
// C3874b.cpp
double main()
{   // C3874
}
```
