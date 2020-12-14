---
description: 詳細については、「コンパイラエラー C3851」を参照してください。
title: コンパイラ エラー C3851
ms.date: 09/05/2018
f1_keywords:
- C3851
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
ms.openlocfilehash: 62f35b8828f7c8f1af9769152a88b7240ff9ff93
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255367"
---
# <a name="compiler-error-c3851"></a>コンパイラ エラー C3851

> '*char*': ユニバーサル文字名で基本文字セットの文字を指定することはできません

## <a name="remarks"></a>解説

C++ としてコンパイルされるコードでは、基本ソース文字セットの文字を表すユニバーサル文字名を使用できません (文字列リテラルまたは文字リテラルの場合を除く)。 詳細については、「 [Character Sets](../../cpp/character-sets.md)」を参照してください。 C としてコンパイルされたコードでは、--0x7f の範囲の文字にユニバーサル文字名を使用することはできません。ただし、0x24 (' $ ')、0x40 (' \@ ')、または 0x60 (' \` ') は除きます。

## <a name="example"></a>例

次の例では、C3851 が生成され、その修正方法が表示されます。

```cpp
// C3851.cpp
int main()
{
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set
   int test2_A = 0;        // OK
}
```
