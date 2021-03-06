---
title: Iterators
ms.date: 11/04/2016
helpviewer_keywords:
- iterator conventions
- C++ Standard Library, iterator conventions
ms.assetid: 2f746be7-b37d-4bfc-bf05-be4336ca982f
ms.openlocfilehash: 3b6713a80244d7063baac2c75ffead76fe93facc
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326500"
---
# <a name="iterators"></a>Iterators

反復子は、C++ 標準ライブラリ コンテナー内の要素を反復処理し、個々の要素へのアクセスを提供するオブジェクトです。 すべての C++ 標準ライブラリ コンテナーに反復子が用意されているため、アルゴリズムではその要素を格納するコンテナーの型を気にせずに標準的な方法で要素にアクセスできます。

反復子を使用して明示的にメンバーとグローバル関数などを使用することができます`begin()`と`end()`などの演算子と**++** と**--** 前方に移動するか、旧バージョンとします。 暗黙的には、範囲も反復子を使用することができます、for ループ、または (一部の反復子の種類)、添字演算子 **\[]** します。

C++ 標準ライブラリでは、シーケンスまたは範囲の始まりが最初の要素になります。 シーケンスまたは範囲の終わりは、常に最後の要素の 1 つ後として定義されます。 グローバル関数`begin`と`end`コンテナーを指定する反復子を返します。 コンテナー内のすべての要素に対する通常の明示的な反復子のループは、次のようになります。

```cpp
vector<int> vec{ 0,1,2,3,4 };
for (auto it = begin(vec); it != end(vec); it++)
{
    // Access element using dereference operator
    cout << *it << " ";
}
```

同じ処理を、range-for ループでより単純に実現できます。

```cpp
for (auto num : vec)
{
    // no deference operator
    cout << num << " ";
}
```

反復子には、5 つのカテゴリがあります。 これらのカテゴリを、機能が低い方から順に示します。

- **出力**。 *出力反復子*`X`できます前方に反復シーケンスを使用して、 **++** 演算子を使用して要素を 1 回だけ書き込むことができ、  __\*__ 演算子。

- **入力**。 *入力反復子*`X`できます前方に反復シーケンスを使用して、+ + 演算子、および要素を読み取れる、時間の任意の数を使用して、 **&ast;** 演算子。 使用して、入力反復子を比較することができます、 **++** と **! =** 演算子。 入力反復子のコピーを増分すると、その他のコピーのいずれも、安全に比較、逆参照、または増分することができなくなります。

- **前方**。 A*前方反復子*`X`を使用してシーケンスを前方に反復処理できます、+ + 演算子との任意の要素を読み取りまたはを使用して非定数要素や回数を書き込み、 **&ast;** 演算子。 使用して要素のメンバーにアクセスすることができます、 **->** 演算子と比較を行う反復子の転送を使用して、 **==** と **! =** 演算子。 前方反復子のコピーを複数作成して、それぞれを個別に逆参照または増分できます。 コンテナーへの参照と呼ばれることがなく初期化された前方反復子を*null 前方反復子*します。 NULL 前方反復子を比較すると、常に等しくなります。

- **双方向**します。 A*双方向反復子*`X`前方反復子の代わりに使用できます。 ことができます、ただしも、双方向反復子としてでデクリメント`--X`、 `X--`、または`(V = *X--)`します。 要素のメンバーにアクセスし、前方反復子と同じ方法で双方向反復子を比較できます。

- **ランダム アクセス**。 A*ランダム アクセス反復子*`X`双方向反復子の代わりに使用できます。 添字演算子を使用するランダム アクセス反復子と **\[]** 要素にアクセスします。 使用することができます、 **+**、 **-**、 **+=** と**-=** 演算子を移動するには前方または後方の要素、および反復子間の距離を計算する、指定された数。 使用して、双方向反復子を比較できる**==**、 **! =**、 **\<**、 **>**、 **\< =** 、および **>=** します。

すべての反復子は、割り当てまたはコピーすることができます。 反復子は軽量のオブジェクトであると見なされ、多くの場合、参照ではなく値によって、渡され、返されます。 前述のすべての操作は、有効な反復子に対して実行したときに例外をスローできないことに注意してください。

反復子のカテゴリの階層は、次の 3 つのシーケンスを表示することによって要約することができます。 シーケンスに対する書き込み専用アクセスの場合、次のいずれの反復子も使用できます。

> 出力反復子<br/>
> 前方反復子を -> します。<br/>
> 双方向反復子を -> します。<br/>
> ランダム アクセス反復子を -> します。<br/>

右矢印は、"後続の反復子で置き換え可能" であることを示します。 出力反復子を必要とするすべてのアルゴリズムは前方反復子を使用してうまく動作しますが、その逆の方法ではうまく動作*しません*。

シーケンスに対する読み取り専用アクセスの場合、次のいずれの反復子も使用できます。

> 入力反復子<br/>
> 前方反復子を -> します。<br/>
> 双方向反復子を -> します。<br/>
> ランダム アクセス反復子を -> します。<br/>

この場合、すべてのカテゴリのうちで最も弱いのは入力反復子です。

最後に、シーケンスに対する読み取り/書き込みアクセスの場合、次のいずれの反復子も使用できます。

> 前方反復子<br/>
> 双方向反復子を -> します。<br/>
> ランダム アクセス反復子を -> します。<br/>

オブジェクト ポインターは、常にランダム アクセス反復子としての機能を果たします。したがって、指定したシーケンスに対する適切な読み取り/書き込みアクセスをサポートしている場合は、反復子の任意のカテゴリとしての機能を果たします。

オブジェクト ポインター以外の反復子 `Iterator` では、特殊化 `iterator_traits<Iterator>` で必要なメンバーの型も定義する必要があります。 これらの要件は、パブリック基底クラス [iterator](../standard-library/iterator-struct.md) から `Iterator` を派生させることによって満たすことができます。

C++ 標準ライブラリのコンテナーとアルゴリズムで反復子がどのように使用されるかを知るには、各反復子カテゴリの約束ごとと制限事項を理解することが必要です。

> [!NOTE]
> range-for ループを使用することにより、反復子の明示的な使用を避けることができます。 詳細については、次を参照してください。[範囲ベースの for ステートメント](../cpp/range-based-for-statement-cpp.md)します。

Visual C には、コンテナーの境界を上書きしないことを確認するには、checked 反復子とデバッグ反復子が用意されています。 詳細については、「[チェックを行う反復子](../standard-library/checked-iterators.md)」および「[デバッグ反復子のサポート](../standard-library/debug-iterator-support.md)」をご覧ください。

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)<br/>
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
