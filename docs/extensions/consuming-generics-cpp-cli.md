---
description: '詳細情報: ジェネリックの使用 (C++/CLI)'
title: ジェネリックの使用 (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], consuming from .NET languages
ms.assetid: e6330ef5-e907-432e-b527-7a22f5899639
ms.openlocfilehash: 3ecfd9f98a8397f96b18ff916bdf9eafe6444a33
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220683"
---
# <a name="consuming-generics-ccli"></a>ジェネリックの使用 (C++/CLI)

ある .NET (または UWP) 言語で作成されたジェネリックを、他の言語で使用できます。 テンプレートとは異なり、コンパイル済みのアセンブリ内のジェネリックは、ジェネリックのままです。 したがって、ジェネリック型が定義されたアセンブリとは別のアセンブリと別の言語で、ジェネリック型をインスタンス化できます。

## <a name="example-generic-class-defined-in-c"></a>例: C で定義されたジェネリッククラス #

### <a name="description"></a>説明

この例では、C# で定義されるジェネリック クラスを示します。

### <a name="code"></a>コード

```csharp
// consuming_generics_from_other_NET_languages.cs
// compile with: /target:library
// a C# program
public class CircularList<ItemType> {
   class ListNode    {
      public ItemType m_item;
      public ListNode next;
      public ListNode(ItemType item) {
         m_item = item;
      }
   }

   ListNode first, last;

   public CircularList() {}

   public void Add(ItemType item) {
      ListNode newnode = new ListNode(item);
      if (first == null) {
         first = last = newnode;
         first.next = newnode;
         last.next = first;
      }
      else {
         newnode.next = first;
         first = newnode;
         last.next = first;
      }
   }

   public void Remove(ItemType item) {
      ListNode iter = first;
      if (first.m_item.Equals( item )) {
         first =
         last.next = first.next;
      }
      for ( ; iter != last ; iter = iter.next )
         if (iter.next.m_item.Equals( item )) {
              if (iter.next == last)
                  last = iter;
              iter.next = iter.next.next;
              return;
          }
   }

   public void PrintAll() {
      ListNode iter = first;
      do {
         System.Console.WriteLine( iter.m_item );
         iter = iter.next;
      } while (iter != last);
   }
}
```

## <a name="example-consume-assembly-authored-in-c"></a>例: C で作成されるアセンブリの使用 #

### <a name="description"></a>説明

この例では、C# で作成されたアセンブリを使用します。

### <a name="code"></a>コード

```cpp
// consuming_generics_from_other_NET_languages_2.cpp
// compile with: /clr
#using <consuming_generics_from_other_NET_languages.dll>
using namespace System;
class NativeClass {};
ref class MgdClass {};

int main() {
   CircularList<int>^ circ1 = gcnew CircularList<int>();
   CircularList<MgdClass^>^ circ2 = gcnew CircularList<MgdClass^>();

   for (int i = 0 ; i < 100 ; i += 10)
      circ1->Add(i);
   circ1->Remove(50);
   circ1->PrintAll();
}
```

```Output
90
80
70
60
40
30
20
10
```

## <a name="see-also"></a>関連項目

[ジェネリック](generics-cpp-component-extensions.md)
