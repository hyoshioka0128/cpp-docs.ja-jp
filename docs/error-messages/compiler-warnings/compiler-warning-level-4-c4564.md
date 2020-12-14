---
description: '詳細情報: コンパイラの警告 (レベル 4) C4564'
title: コンパイラの警告 (レベル 4) C4564
ms.date: 11/04/2016
f1_keywords:
- C4564
helpviewer_keywords:
- C4564
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
ms.openlocfilehash: 112d1d20d34619d7a39d20c7fcd5f21584730cef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255172"
---
# <a name="compiler-warning-level-4-c4564"></a>コンパイラの警告 (レベル 4) C4564

クラス ' class ' のメソッド ' method ' で、サポートされていない既定のパラメーター ' parameter ' が定義されています

コンパイラは、既定値を持つ1つ以上のパラメーターを持つメソッドを検出しました。 パラメーターの既定値は、メソッドが呼び出されるときに無視されます。これらのパラメーターの値を明示的に指定します。 これらのパラメーターの値を明示的に指定しないと、C++ コンパイラによってエラーが生成されます。

次の .dll を Visual Basic で作成した場合、メソッドの引数に既定のパラメーターを使用できます。

```vb
' C4564.vb
' compile with: vbc /t:library C4564.vb
Public class TestClass
   Public Sub MyMethod (a as Integer, _
                        Optional c as Integer=1)
   End Sub
End class
```

次の C++ のサンプルでは、Visual Basic で作成された .dll を使用しています。

```cpp
// C4564.cpp
// compile with: /clr /W4 /WX
#using <C4564.dll>

int main() {
   TestClass ^ myx = gcnew TestClass();   // C4564
   myx->MyMethod(9);
   // try the following line instead, to avoid an error
   // myx->MyMethod(9, 1);
}
```
