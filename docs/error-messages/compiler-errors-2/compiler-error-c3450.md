---
description: 詳細については、「コンパイラエラー C3450」を参照してください。
title: コンパイラ エラー C3450
ms.date: 11/04/2016
f1_keywords:
- C3450
helpviewer_keywords:
- C3450
ms.assetid: 78892cf7-0b82-4589-90d0-e06666247003
ms.openlocfilehash: e56382a3f71b59fee42b6a545318cf3846e1a1f7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316051"
---
# <a name="compiler-error-c3450"></a>コンパイラ エラー C3450

'type': 属性ではありません。[System::AttributeUsageAttribute] または [Windows::Foundation::Metadata::AttributeUsageAttribute] を指定できません

ユーザー定義のマネージド属性は <xref:System.ComponentModel.AttributeCollection.%23ctor%2A> から継承する必要があります。 Windows ランタイム属性は、`Windows::Foundation::Metadata` 名前空間で定義する必要があります。

詳細については、「 [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>例

次の例では、C3450 を生成し、その修正方法を示しています。

```cpp
// C3450.cpp
// compile with: /clr
// C3450 expected
using namespace System;
using namespace System::Security;
using namespace System::Security::Permissions;

public ref class MyClass {};

class MyClass2 {};

[attribute(AttributeTargets::All)]
ref struct AtClass {
   AtClass(Type ^) {}
};

[attribute(AttributeTargets::All)]
ref struct AtClass2 {
   AtClass2() {}
};

// Apply the AtClass and AtClass2 attributes to class B
[AtClass(MyClass::typeid), AtClass2]
[AttributeUsage(AttributeTargets::All)]
// Delete the following line to resolve.
ref class B {};
// Uncomment the following line to resolve.
// ref class B : Attribute {};
```
