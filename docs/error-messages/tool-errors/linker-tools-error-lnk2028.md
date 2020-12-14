---
description: 詳細については、「リンカツール Error LNK2028」を参照してください。
title: リンカ ツール エラー LNK2028
ms.date: 11/04/2016
f1_keywords:
- LNK2028
helpviewer_keywords:
- LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
ms.openlocfilehash: 31b20cc572a44b1260f58eb03519b60050c0246c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275725"
---
# <a name="linker-tools-error-lnk2028"></a>リンカ ツール エラー LNK2028

"*exported_function*" (*decorated_name*) が関数 "*function_containing_function_call*" で参照されています (*decorated_name*)

## <a name="remarks"></a>解説

ネイティブ関数を純粋なイメージにインポートしようとすると、暗黙的な呼び出し規約がネイティブコンパイルと純粋コンパイルで異なることに注意してください。

**/Clr: pure** コンパイラオプションは visual studio 2015 で非推奨とされており、visual studio 2017 ではサポートされていません。

## <a name="examples"></a>例

このコードサンプルでは、エクスポートされたネイティブ関数を持つコンポーネントを生成します。この関数の呼び出し規約は、暗黙的に [__cdecl](../../cpp/cdecl.md)ます。

```cpp
// LNK2028.cpp
// compile with: /LD
__declspec(dllexport) int func() {
   return 3;
}
```

次の例では、ネイティブ関数を使用する純粋なクライアントを作成します。 ただし、 **/clr: pure** の呼び出し規約は [__clrcall](../../cpp/clrcall.md)。 次の例では、LNK2028 が生成されます。

```cpp
// LNK2028_b.cpp
// compile with: /clr:pure lnk2028.lib
// LNK2028 expected
int func();

int main() {
   return func();
}
```
