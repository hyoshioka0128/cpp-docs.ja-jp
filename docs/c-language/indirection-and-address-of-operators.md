---
description: '詳細情報: 間接演算子とアドレス演算子'
title: 間接演算子とアドレス演算子
ms.date: 02/16/2018
helpviewer_keywords:
- address-of operator (&)
- '* operator'
- operators [C++], address-of
- ampersand operator (&)
- '* operator, indirection operator'
- addresses [C++], indirection
- addresses [C++]
- indirection operator
- '& operator, address-of operator'
- null pointers [C++]
- '* operator, address-of operator'
- operators [C++], indirection
ms.assetid: 10d62b00-12ba-4ea9-a2d5-09ac29ca2232
ms.openlocfilehash: bd05d9eee4a453d9d99198a1a8481fcebcf103dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137594"
---
# <a name="indirection-and-address-of-operators"></a>間接演算子とアドレス演算子

単項間接演算子 ( __&#42;__ ) は、ポインターを介して値に間接的にアクセスします。 オペランドは、ポインター型である必要があります。 演算の結果は、オペランドによってアドレス指定される値です。つまり、オペランドがポイントするアドレスでの値です。 結果の型は、オペランドでアドレス指定する型です。

オペランドの型が *pointer to type* である場合、関節演算子の結果は *type* になります。 オペランドが関数を指している場合、結果は関数指定子になります。 オブジェクトを指している場合、結果はオブジェクトを指定する左辺値になります。

ポインター値が有効でない場合は、間接演算子の結果が定義されません。 ポインター値が無効になる一般的な条件をいくつか示します。

- ポインターが null ポインターです。

- ポインターは、参照時に有効期間終了後のオブジェクト (スコープ外になったオブジェクトや割り当てが解除されたオブジェクトなど) のアドレスを指定します。

- ポインターが、指されているオブジェクトの型ではアラインメントが不適切なアドレスを指定しています。

- ポインターが、実行プログラムで使用されていないアドレスを指定しています。

単項アドレス演算子 ( **&** ) は、オペランドのアドレスを与えます。 オペランドは __レジスタ__ を宣言していなく、ビット フィールドでないオブジェクトを指定する左辺値か、単項 __&#42;__ 演算子または配列逆参照 ( __&#91;&#93;__ ) 演算子、または関数指定子の結果のどちらかである必要があります。 結果は、型 *type* のオペランドに対する型 *pointer to type* です。

オペランドが単項 __&#42;__ 演算子の結果である場合、演算子は評価されず、両方が省略されたかのような結果になります。 結果は左辺値ではなく、演算子の制約が引き続き適用されます。 オペランドが __&#91;&#93;__ の結果である場合、 __&__ 演算子も、 __&#91;&#93;__ 演算子によって暗黙的に指定される単項 __&#42;__ も評価されません。 結果は __&__ 演算子を削除して __&#91;&#93;__ 演算子を __+__ 演算子に変更する場合と同じ効果があります。 それ以外の場合、結果はオブジェクトへのポインターまたは演算子によって指定された関数になります。

## <a name="examples"></a>使用例

以下に挙げる例では、次の一般的な宣言を使用します。

```C
int *pa, x;
int a[20];
double d;
```

このステートメントは address-of 演算子 ( **&** ) を使用して、配列 `a` の 6 番目の要素のアドレスを受け取ります。 結果は、ポインター変数 `pa` に格納されます。

```C
pa = &a[5];
```

この例では、間接参照演算子 ( __&#42;__ ) は、`pa` に格納されているアドレスにある **`int`** 値にアクセスするために使用されます。 その値は整数変数 `x` に代入されます。

```C
x = *pa;
```

この例では、`x` のアドレスに間接演算子を適用した結果が `x` と同じであることが示されます。

```C
assert( x == *&x );
```

この例では、関数へのポインターを宣言するのと同じ方法を示しています。

```C
int roundup( void );     /* Function declaration */

int  *proundup  = roundup;
int  *pround  = &roundup;
assert( pround == proundup );
```

関数 `roundup` を宣言した後、`roundup` への 2 つのポインターを宣言して、初期化しています。 最初のポインター、`proundup` は、関数名のみを使用して初期化され、2 番目のポインター、`pround` は、初期化時にアドレス演算子が使用されています。 これらの初期化は同じ意味を持ちます。

## <a name="see-also"></a>関連項目

[間接演算子: &#42;](../cpp/indirection-operator-star.md)<br/>
[address-of 演算子: &](../cpp/address-of-operator-amp.md)
