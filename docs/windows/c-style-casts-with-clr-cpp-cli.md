---
title: C スタイル キャストと/clr (C +/cli CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- C-style casts and /clr
ms.assetid: d2a4401a-156a-4da9-8d12-923743e26913
ms.openlocfilehash: abbcd61f8c86709e16958e4220c0ea96e393c8bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447074"
---
# <a name="c-style-casts-with-clr-ccli"></a>C スタイル キャストと /clr (C++/CLI)

次のトピックでは、共通言語ランタイムにのみ適用されます。

CLR 型で使用すると、コンパイラは C スタイルのキャストの次の順序で、以下のいずれかにキャストをマップしようとします。

1. const_cast

2. safe_cast

3. safe_cast plus const_cast

4. static_cast

5. static_cast plus const_cast

キャストの上に示したが、有効な場合、および式の型とターゲットの型が CLR 参照型である場合は、C スタイル キャストは実行時チェック (castclass MSIL 命令) にマップします。 それ以外の場合、C スタイル キャストは無効とみなされ、コンパイラがエラーを発行します。

## <a name="remarks"></a>Remarks

C スタイル キャストは推奨されません。 コンパイルするときに[/clr (共通言語ランタイムのコンパイル)](../build/reference/clr-common-language-runtime-compilation.md)を使用して、 [safe_cast](../windows/safe-cast-cpp-component-extensions.md)します。

次の例は、C スタイルのキャストにマップされる、 **const_cast**します。

```cpp
// cstyle_casts_1.cpp
// compile with: /clr
using namespace System;

ref struct R {};
int main() {
   const R^ constrefR = gcnew R();
   R^ nonconstR = (R^)(constrefR);
}
```

次の例は、C スタイルのキャストにマップされる、 **safe_cast**します。

```cpp
// cstyle_casts_2.cpp
// compile with: /clr
using namespace System;
int main() {
   Object ^ o = "hello";
   String ^ s = (String^)o;
}
```

次の例は、C スタイルのキャストにマップされる、 **safe_cast** plus **const_cast**します。

```cpp
// cstyle_casts_3.cpp
// compile with: /clr
using namespace System;

ref struct R {};
ref struct R2 : public R {};

int main() {
   const R^ constR2 = gcnew R2();
   try {
   R2^ b2DR = (R2^)(constR2);
   }
   catch(InvalidCastException^ e) {
      System::Console::WriteLine("Invalid Exception");
   }
}
```

次の例は、C スタイルのキャストにマップされる、 **static_cast**します。

```cpp
// cstyle_casts_4.cpp
// compile with: /clr
using namespace System;

struct N1 {};
struct N2 {
   operator N1() {
      return N1();
   }
};

int main() {
   N2 n2;
   N1 n1 ;
   n1 = (N1)n2;
}
```

次の例は、C スタイルのキャストにマップされる、 **static_cast** plus **const_cast**します。

```cpp
// cstyle_casts_5.cpp
// compile with: /clr
using namespace System;
struct N1 {};

struct N2 {
   operator const N1*() {
      static const N1 n1;
      return &n1;
   }
};

int main() {
   N2 n2;
   N1* n1 = (N1*)(const N1*)n2;   // const_cast + static_cast
}
```

次の例を C スタイルのキャストを実行時チェックにマップします。

```cpp
// cstyle_casts_6.cpp
// compile with: /clr
using namespace System;

ref class R1 {};
ref class R2 {};

int main() {
   R1^ r  = gcnew R1();
   try {
      R2^ rr = ( R2^)(r);
   }
   catch(System::InvalidCastException^ e) {
      Console::WriteLine("Caught expected exception");
   }
}
```

次の例では、無効な C スタイルのキャスト、これにより、コンパイラ エラーを発行します。

```cpp
// cstyle_casts_7.cpp
// compile with: /clr
using namespace System;
int main() {
   String^s = S"hello";
   int i = (int)s;   // C2440
}
```

## <a name="requirements"></a>必要条件

コンパイラ オプション: `/clr`

## <a name="see-also"></a>関連項目

[Component Extensions for .NET と UWP](../windows/component-extensions-for-runtime-platforms.md)