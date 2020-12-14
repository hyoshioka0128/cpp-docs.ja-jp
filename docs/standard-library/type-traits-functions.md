---
description: '詳細情報: &lt; type_traits &gt; 関数'
title: '&lt;type_traits&gt; 関数'
ms.date: 11/04/2016
ms.assetid: dce4492f-f3e4-4d5e-bdb4-5875321254ec
helpviewer_keywords:
- std::is_assignable
- std::is_copy_assignable
- std::is_copy_constructible
- std::is_default_constructible
- std::is_move_assignable
- std::is_move_constructible
- std::is_nothrow_move_assignable
- std::is_trivially_copy_assignable
- std::is_trivially_move_assignable
- std::is_trivially_move_constructible
ms.openlocfilehash: a1608ddc9d846ca9e8e851ef67d390aebb6f840e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253326"
---
# <a name="lttype_traitsgt-functions"></a>&lt;type_traits&gt; 関数

[is_assignable](#is_assignable)\
[is_copy_assignable](#is_copy_assignable)\
[is_copy_constructible](#is_copy_constructible)\
[is_default_constructible](#is_default_constructible)\
[is_move_assignable](#is_move_assignable)\
[is_move_constructible](#is_move_constructible)\
[is_nothrow_move_assignable](#is_nothrow_move_assignable)\
[is_nothrow_swappable](#is_nothrow_swappable)\
[is_nothrow_swappable_with](#is_nothrow_swappable_with)\
[is_swappable](#is_swappable)\
[is_swappable_with](#is_swappable_with)\
[is_trivially_copy_assignable](#is_trivially_copy_assignable)\
[is_trivially_move_assignable](#is_trivially_move_assignable)\
[is_trivially_move_constructible](#is_trivially_move_constructible)

## <a name="is_assignable"></a><a name="is_assignable"></a> is_assignable

型の値を型 *から* 型 *に* 割り当てることができるかどうかをテストします。

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>パラメーター

*宛先*\
代入を受け取るオブジェクトの型。

*差出人*\
値を渡すオブジェクトの型。

### <a name="remarks"></a>解説

評価されていない式 `declval<To>() = declval<From>()` は整形式である必要があります。 と *の* どちらも、完全な型、 **`void`** 、または不明なバインドの配列である必要があります。

## <a name="is_copy_assignable"></a><a name="is_copy_assignable"></a> is_copy_assignable

割り当て時に型をコピーできるかどうかをテストします。

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>パラメーター

*~*\
照会する型。

### <a name="remarks"></a>解説

型 *Ty* がコピー代入演算子を持つクラスである場合、型述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。 Is_assignable と同じ \<Ty&, const Ty&> です。

## <a name="is_copy_constructible"></a><a name="is_copy_constructible"></a> is_copy_constructible

型にコピー コンストラクターが存在するかどうかをテストします。

```cpp
template <class Ty>
struct is_copy_constructible;
```

### <a name="parameters"></a>パラメーター

*~*\
照会する型。

### <a name="remarks"></a>解説

型 *Ty* がコピーコンストラクターを持つクラスである場合、型述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。

### <a name="example"></a>例

```cpp
#include <type_traits>
#include <iostream>

struct Copyable
{
    int val;
};

struct NotCopyable
{
   NotCopyable(const NotCopyable&) = delete;
   int val;

};

int main()
{
    std::cout << "is_copy_constructible<Copyable> == " << std::boolalpha
        << std::is_copy_constructible<Copyable>::value << std::endl;
    std::cout << "is_copy_constructible<NotCopyable> == " << std::boolalpha
        << std::is_copy_constructible<NotCopyable>::value << std::endl;

    return (0);
}
```

```Output
is_copy_constructible<Copyable> == true
is_copy_constructible<NotCopyable > == false
```

## <a name="is_default_constructible"></a><a name="is_default_constructible"></a> is_default_constructible

型が既定のコンストラクターを持つかどうかをテストします。

```cpp
template <class Ty>
struct is_default_constructible;
```

### <a name="parameters"></a>パラメーター

*\T*\
照会する型。

### <a name="remarks"></a>解説

型 *T* が既定のコンストラクターを持つクラス型である場合、型述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。 これは、述語 `is_constructible<T>`と同じです。 型 *T* は完全な型、 **`void`** 、または不明なバインドの配列である必要があります。

### <a name="example"></a>例

```cpp
#include <type_traits>
#include <iostream>

struct Simple
{
    Simple() : val(0) {}
    int val;
};

struct Simple2
{
    Simple2(int v) : val(v) {}
    int val;
};

int main()
{
    std::cout << "is_default_constructible<Simple> == " << std::boolalpha
        << std::is_default_constructible<Simple>::value << std::endl;
    std::cout << "is_default_constructible<Simple2> == " << std::boolalpha
        << std::is_default_constructible<Simple2>::value << std::endl;

    return (0);
}
```

```Output
is_default_constructible<Simple> == true
is_default_constructible<Simple2> == false
```

## <a name="is_move_assignable"></a><a name="is_move_assignable"></a> is_move_assignable

型が移動代入可能であるかどうかをテストします。

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>パラメーター

*\T*\
照会する型。

### <a name="remarks"></a>解説

型への右辺値参照を型の参照に割り当てる事ができる場合、その型は移動代入可能です。 型述語は `is_assignable<T&, T&&>` と同じです。 移動代入できる型には、コンパイラにより生成された移動代入演算子またはユーザー定義の移動代入演算子を含む参照可能なスカラー型やクラス型があります。

## <a name="is_move_constructible"></a><a name="is_move_constructible"></a> is_move_constructible

型に移動コンストラクターが存在するかどうかをテストします。

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>パラメーター

*\T*\
評価される型

### <a name="remarks"></a>解説

移動操作を使用して型 *T* を構築できる場合は true に評価される型述語。 この述語は `is_constructible<T, T&&>` と同じです。

## <a name="is_nothrow_move_assignable"></a><a name="is_nothrow_move_assignable"></a> is_nothrow_move_assignable

型に移動代入演算子があるかどうかをテスト **`nothrow`** します。

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>パラメーター

*~*\
照会する型。

### <a name="remarks"></a>解説

型が nothrow の移動代入演算子 *を持つ場合* 、型の述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。

## <a name="is_nothrow_swappable"></a><a name="is_nothrow_swappable"></a> is_nothrow_swappable

```cpp
template <class T> struct is_nothrow_swappable;
```

## <a name="is_nothrow_swappable_with"></a><a name="is_nothrow_swappable_with"></a> is_nothrow_swappable_with

```cpp
template <class T, class U> struct is_nothrow_swappable_with;
```

## <a name="is_swappable"></a><a name="is_swappable"></a> is_swappable

```cpp
template <class T> struct is_swappable;
```

## <a name="is_swappable_with"></a><a name="is_swappable_with"></a> is_swappable_with

```cpp
template <class T, class U> struct is_swappable_with;
```

## <a name="is_trivially_copy_assignable"></a><a name="is_trivially_copy_assignable"></a> is_trivially_copy_assignable

型が自明なコピー代入演算子を持つかどうかをテストします。

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>パラメーター

*\T*\
照会する型。

### <a name="remarks"></a>解説

型 *T* が自明なコピー代入演算子を持つクラスである場合、型述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。

クラス *t* の割り当てコンストラクターは、暗黙的に指定されている場合、クラス *t に* 仮想関数がない場合、 *クラス t に* 仮想基底クラスがない場合、クラス型のすべての非静的データメンバーのクラスに自明な代入演算子がある場合、クラスの型配列のすべての非静的データメンバーのクラスに自明な代入演算子があります。

## <a name="is_trivially_move_assignable"></a><a name="is_trivially_move_assignable"></a> is_trivially_move_assignable

型が自明なムーブ代入演算子を持つかどうかをテストします。

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>パラメーター

*~*\
照会する型。

### <a name="remarks"></a>解説

型 *Ty* が自明なムーブ代入演算子を持つクラスである場合、型述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。

クラス *Ty* の移動代入演算子は、次のような場合に自明です。

暗黙的に指定されている

クラス *Ty* に仮想関数がありません。

クラス *Ty* に仮想基底がありません

クラス型のすべての非静的データ メンバーのクラスに自明なムーブ代入演算子がある

クラスの型配列のすべての非静的データ メンバーのクラスに自明なムーブ代入演算子がある

## <a name="is_trivially_move_constructible"></a><a name="is_trivially_move_constructible"></a> is_trivially_move_constructible

型に自明な移動コンストラクターが存在するかどうかをテストします。

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>パラメーター

*~*\
照会する型。

### <a name="remarks"></a>解説

型 *Ty* が自明な移動コンストラクターを持つクラスである場合、型述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。

クラス *Ty* の移動コンストラクターは、次のような場合に自明です。

暗黙的に宣言されている

そのパラメーターの型が暗黙的な宣言のものと同じである

クラス *Ty* に仮想関数がありません。

クラス *Ty* に仮想基底がありません

クラスに揮発性の非静的データ メンバーがない

*クラスの* すべての直接基底に自明な移動コンストラクターがある

クラス型のすべての非静的データ メンバーのクラスに自明な移動コンストラクターがある

クラスの型配列のすべての非静的データ メンバーのクラスに自明な移動コンストラクターがある

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
