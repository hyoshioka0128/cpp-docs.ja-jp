---
title: '方法: MSIL からスローされるネイティブ コードの例外をキャッチする'
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions, catching
- catching exceptions, thrown from MSIL
- MSIL, catching exceptions in native code
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
ms.openlocfilehash: 73c9a9af66a6e292c76b96ec47a5853684e602f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635613"
---
# <a name="how-to-catch-exceptions-in-native-code-thrown-from-msil"></a>方法: MSIL からスローされるネイティブ コードの例外をキャッチする

ネイティブ コードでは、MSIL からネイティブの C++ 例外をキャッチできます。  CLR の例外をキャッチする`__try`と`__except`します。

詳細については、次を参照してください。[構造化例外処理 (c/c++)](../cpp/structured-exception-handling-c-cpp.md)と[C++ 例外処理](../cpp/cpp-exception-handling.md)します。

## <a name="example"></a>例

次の例では、MSIL 例外をスローする 2 つの関数、別およびネイティブの例外をスローする 1 つのモジュールを定義します。

```
// catch_MSIL_in_native.cpp
// compile with: /clr /c
void Test() {
   throw ("error");
}

void Test2() {
   throw (gcnew System::Exception("error2"));
}
```

## <a name="example"></a>例

次の例では、ネイティブおよび MSIL の例外をキャッチするモジュールを定義します。

```
// catch_MSIL_in_native_2.cpp
// compile with: /clr catch_MSIL_in_native.obj
#include <iostream>
using namespace std;
void Test();
void Test2();

void Func() {
   // catch any exception from MSIL
   // should not catch Visual C++ exceptions like this
   // runtime may not destroy the object thrown
   __try {
      Test2();
   }
   __except(1) {
      cout << "caught an exception" << endl;
   }

}

int main() {
   // catch native C++ exception from MSIL
   try {
      Test();
   }
   catch(char * S) {
      cout << S << endl;
   }
   Func();
}
```

```Output
error
caught an exception
```

## <a name="see-also"></a>関連項目

[例外処理](../windows/exception-handling-cpp-component-extensions.md)