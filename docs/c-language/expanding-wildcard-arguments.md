---
title: ワイルドカード引数の展開
ms.date: 11/04/2016
helpviewer_keywords:
- asterisk wildcard
- question mark, wildcard
- expanding wildcard arguments
- wildcards, expanding
ms.assetid: 80a11c4b-0199-420e-a342-cf1d803be5bc
ms.openlocfilehash: 2224d01eeb3ec54a9c0ff895dfa45574135f7c0c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443421"
---
# <a name="expanding-wildcard-arguments"></a>ワイルドカード引数の展開

**Microsoft 固有の仕様**

C プログラムを実行する際、コマンド ラインのファイル名引数とパス引数の指定に、2 つのワイルドカード (疑問符 (?) およびアスタリスク (*)) のいずれかを使用できます。

既定では、ワイルドカードはコマンドラインの引数では展開されません。 setargv.obj または wsetargv.obj ファイルとリンクしてワイルドカードを展開し、標準の引数ベクターの `argv` 読み込みルーチンをワイルドカードを展開するバージョンと置き換えることができます。 プログラムが `main` 関数を使用している場合は、setargv.obj とリンクします。プログラムが `wmain` 関数を使用している場合は、wsetargv.obj とリンクします。これら両方の動作は同等です。

setargv.obj または wsetargv.obj とリンクするには、 **/link** オプションを使用します。 例:

**cl example.c /link setargv.obj**

ワイルドカードはオペレーティング システム コマンドと同じように展開されます (ワイルドカードの使用経験がない場合は、オペレーティング システムのユーザー ガイドを参照)。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>参照

[リンク オプション](../c-runtime-library/link-options.md)<br/>
[main 関数とプログラム実行](../c-language/main-function-and-program-execution.md)