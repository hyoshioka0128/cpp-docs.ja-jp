---
title: リンカ ツール エラー LNK2001
ms.date: 05/17/2017
f1_keywords:
- LNK2001
helpviewer_keywords:
- LNK2001
ms.assetid: dc1cf267-c984-486c-abd2-fd07c799f7ef
ms.openlocfilehash: dba197be71fc77af6d95c2ec62053928ac1627cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631661"
---
# <a name="linker-tools-error-lnk2001"></a>リンカ ツール エラー LNK2001

未解決の外部シンボル"*シンボル*"

コンパイル済みのコードは、参照またはへの呼び出しにより、*シンボル*が、そのシンボルが、ライブラリをリンカーに指定されたオブジェクト ファイルのいずれかで定義されていません。

このエラー メッセージの致命的なエラーが続く[LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md)します。 エラー LNK1120 を解決するすべての LNK2001 と LNK2019 エラーを修正する必要があります。

## <a name="possible-causes"></a>考えられる原因

このエラーを取得する方法はたくさんありますが、関数または変数のリンカーへの参照が含まれるすべての*を解決する*、またはの定義を検索します。 コンパイラがシンボルがないときに特定できます*宣言*がない場合ではありません*定義*異なるソース ファイルまたはライブラリで定義があるので、します。 シンボル参照が定義されていることはありません、リンカーはエラーを生成します。

### <a name="coding-issues"></a>コーディングの問題

一致しない場合、ソース コードまたはモジュール定義 (.def) によってこのエラーは発生するファイル。 たとえば、変数の名前を付ける場合`var1`で 1 つの C++ ソース ファイルととしてアクセスを試みる`VAR1`別、このエラーが生成されます。 この問題を解決するには、使用は一貫してスペルし、名前、大文字と小文字します。

このエラーは、使用するプロジェクトで発生することができます[関数のインライン化](../../error-messages/tool-errors/function-inlining-problems.md)ヘッダー ファイルではなく、ソース ファイル内の関数を定義する場合。 それらを定義するソース ファイルの外部関数のインライン展開を表示できません。 この問題を解決するには、宣言されているヘッダーにインライン関数を定義します。

使用せず、C プログラムから C 関数を呼び出す場合は、このエラーを発生することができます、 `extern "C"` C 関数の宣言。 コンパイラは C および C++ コードでは、さまざまな内部シンボルの名前付け規則を使用して、シンボルを解決するときに、リンカーを検索する内部シンボルの名前です。 この問題を解決するには、使用、`extern "C"`コンパイラが、これらのシンボルを C 内部の名前付け規則を使用する C++ コードで使う C 関数のすべての宣言のラッパーです。 コンパイラ オプション[/Tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)と[/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)コンパイラがファイル名拡張子に関係なく、C++ または C としてファイルをコンパイルします。 これらのオプションには、内部の関数名が予期したものと異なる可能性があります。

このエラーは、関数または外部リンケージがないデータを参照しようとして発生することができます。 C++ では、インライン関数と`const`として明示的に指定しない限り、データが内部リンケージを持ちます`extern`します。 この問題を解決するには明示的な使用`extern`定義のソース ファイルの外部参照シンボルを宣言します。

このエラーは、によって発生することができます、[関数本体または変数が不足している](../../error-messages/tool-errors/missing-function-body-or-variable.md)定義します。 このエラーが、宣言しますが、ない、変数、関数、またはクラス コードで定義する際に一般的です。 コンパイラが必要なだけ関数プロトタイプまたは`extern`関数のコードまたは変数の領域がないために、エラー、せず、リンカーのオブジェクト ファイルを生成する変数の宣言が関数への呼び出しや、変数への参照を解決できません予約されています。 この問題を解決するには、すべての参照先の関数と変数完全に定義されているソース ファイルまたはライブラリをリンクに含まれていることを確認します。

このエラーは、戻り値およびパラメーター型または関数定義と一致しない呼び出し規約を使用して関数呼び出しによって発生することができます。 オブジェクトの C++ ファイルで[名前装飾](../../error-messages/tool-errors/name-decoration.md)呼び出し規則、クラスまたは名前空間スコープ、および関数の戻り値およびパラメーターの型を使用するように呼び出しをときは一致するシンボルを最終の装飾関数名に組み込まれていますその他のオブジェクト ファイルからの関数は解決されます。 この問題を解決するには、同じスコープ、型、および呼び出し規約の宣言、定義、およびすべての関数の呼び出しを使用することを確認します。

このエラーはクラス定義の関数プロトタイプが含まれますに失敗する場合に、C++ コードで発生することができます[実装が含まれて](../../error-messages/tool-errors/missing-function-body-or-variable.md)関数のし、呼び出す。 この問題を解決するには、クラスのメンバーの宣言と呼ばれるすべての定義を指定することを確認します。

このエラーは、抽象基本クラスから純粋仮想関数を呼び出そうとすると、発生することができます。 純粋仮想関数には、基底クラスの実装がありません。 この問題を解決するには、仮想関数を呼び出すすべて実装されていることを確認します。

このエラーは、関数内で宣言された変数を使用しようとして発生することができます ([ローカル変数](../../error-messages/tool-errors/automatic-function-scope-variables.md)) その関数の範囲外です。 この問題を解決するには、スコープ、されていない変数への参照を削除または変数を上位のスコープに移動します。

ATL プロジェクトのリリース バージョンをビルドすると、CRT のスタートアップ コードが必要であるメッセージの生成時に、このエラーが発生することができます。 この問題を解決で、次のいずれかの操作を実行するには

- 削除`_ATL_MIN_CRT`CRT スタートアップ コードが含まれるようにプリプロセッサの一覧から定義します。 参照してください[[全般] プロパティ ページ (プロジェクト)](../../ide/general-property-page-project.md)詳細についてはします。

- 可能であれば、CRT のスタートアップ コードを必要とする CRT 関数の呼び出しを削除します。 代わりに、対応する win32 関数を使用します。 たとえば、使用して`lstrcmp`の代わりに`strcmp`します。 CRT のスタートアップ コードが必要な既知の関数では、文字列および浮動小数点関数の一部を示します。

### <a name="compilation-and-link-issues"></a>コンパイルとリンクの問題

プロジェクトで、ライブラリへの参照が不足しているときに、このエラーが発生することができます (します。LIB) またはオブジェクト (します。OBJ) ファイルです。 この問題を解決するには、プロジェクトに必要なライブラリまたはオブジェクト ファイルへの参照を追加します。 詳細については、次を参照してください。[リンカー入力としての .lib ファイル](../../build/reference/dot-lib-files-as-linker-input.md)します。

このエラーは、使用する場合に発生することができます、 [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)または[/Zl](../../build/reference/zl-omit-default-library-name.md)オプション。 これらのオプションを指定すると 明示的に含めていた場合を除き、プロジェクトに必要なコードが含まれているライブラリはリンクされません。 この問題を解決するには、リンクのコマンドラインを使用するすべてのライブラリを明示的に含めます。 これらのオプションを使用すると、多くの不足している CRT または標準ライブラリ関数名が表示された場合、リンクに、CRT と標準ライブラリの Dll またはライブラリ ファイルを明示的に含めます。

使用してコンパイルする場合、 **/clr**オプション、.cctor に不足している参照があります。 この問題を解決するを参照してください。[混在アセンブリの初期化](../../dotnet/initialization-of-mixed-assemblies.md)詳細についてはします。

このエラーは、アプリケーションのデバッグ バージョンを構築するときに、リリース モードのライブラリにリンクする場合に発生することができます。 同様に、オプションを使用する場合 **/MTd**または **/MDd**定義または`_DEBUG`とリリース ライブラリをリンクし、その他の問題の多く潜在的な未解決の外部項目を想定する必要があります。 ような問題が発生もデバッグ ライブラリとリリース モードのビルドをリンクします。 この問題を解決するには、デバッグ ビルドでデバッグ ライブラリを使用して、retail 小売ライブラリのビルドを確認します。

ライブラリの 1 つのバージョンからシンボルをコードから参照が、リンカー、ライブラリの別のバージョンを指定する場合、このエラーが発生することができます。 一般に、オブジェクト ファイルまたは別のバージョンのコンパイラに組み込まれているライブラリを混在させることはできません。 新しいバージョンに含まれているライブラリには、以前のバージョン、およびその逆に含まれているライブラリ内に見つかりませんシンボルを含めることができます。 この問題を解決するには、それらをまとめてリンクする前にすべてのオブジェクト ファイルと同じバージョンのコンパイラとライブラリをビルドします。

- ツール&#124;オプション&#124;プロジェクト&#124;vc++ ディレクトリ ダイアログで ライブラリ ファイルの選択 では、ライブラリの検索順序を変更できます。 プロジェクトのプロパティ ページ ダイアログ ボックスの リンカー フォルダーは、最新でない可能性があるパスを含めることもできます。

- この問題には、(おそらく、別の場所に) 新しい SDK がインストールされているし、新しい場所を指す検索順序が更新されない場合があります。 通常、パスを新しい SDK に配置する必要がありますが含まれ、lib の既定の Visual C の場所の前にディレクトリ。 また、埋め込みのパスを含むプロジェクトは、まだ有効では、別の場所にインストールされている新しいバージョンで追加された新機能の期限切れを古いパスにポイントです。

- コマンドラインでビルドし、独自の環境変数を作成した場合は、ツール、ライブラリ、およびヘッダー ファイルへのパスを一貫したバージョンに移動することを確認します。 詳細については、次を参照してください[コマンド ライン ビルドのパスと環境変数を設定する。](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)

現在の標準はありません[C++ の名前付け](../../error-messages/tool-errors/name-decoration.md)コンパイラ ベンダー間またはコンパイラの異なるバージョン間であってもします。 そのため、他のコンパイラでコンパイルされたオブジェクト ファイルをリンク可能性があります、同じ名前付けスキームが生成されず、エラー LNK2001 が発生するため。

[コンパイル オプションのミキシングのインラインと非インライン](../../error-messages/tool-errors/function-inlining-problems.md)モジュールごとに異なることができます、lnk2001 します。 関数のインライン化がオンで C++ のライブラリが作成されたかどうか (**/Ob1**または **/Ob2**) 関数を記述する、対応するヘッダー ファイルがインライン化を無効になっていますが、(ありません`inline`キーワード)、このエラー発生します。 この問題を解決する関数を定義する`inline`ヘッダー ファイルを他のソース ファイルが含まれます。

使用する場合、`#pragma inline_depth`があるコンパイラ ディレクティブを確認してください、 [2 以上のセットの値](../../error-messages/tool-errors/function-inlining-problems.md)、使用することも確認して、 [/Ob1](../../build/reference/ob-inline-function-expansion.md)または[/Ob2](../../build/reference/ob-inline-function-expansion.md)コンパイラ オプション。

このエラーは、リンクを省略した場合に発生する可能性が/NOENTRY をリソース専用 DLL を作成するときにオプションします。 この問題を解決するには、リンクのコマンドに/NOENTRY オプションを追加します。

このエラーは、プロジェクトに正しくない/SUBSYSTEM または/ENTRY 設定を使用する場合に発生することができます。 たとえば、コンソール アプリケーションを作成し、/SUBSYSTEM:WINDOWS を指定すると、未解決の外部エラーが生成の`WinMain`します。 この問題を解決するには、プロジェクトの種類にオプションの一致を確認します。 これらのオプションとエントリ ポイントの詳細については、次を参照してください。、 [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)と[/ENTRY](../../build/reference/entry-entry-point-symbol.md)リンカー オプション。

### <a name="exported-symbol-issues"></a>エクスポートされたシンボルの問題

このエラーは、.def ファイルに一覧表示、エクスポートが見つからなかった場合に発生します。 存在しない、スペルが正しいか、C の装飾名を使用する可能性があります。 .Def ファイルは、装飾名を取得しません。 この問題を解決する不要なエクスポートを削除し、使用`extern "C"`エクスポートされたシンボルを宣言します。

## <a name="what-is-an-unresolved-external-symbol"></a>未解決の外部シンボルとは何ですか。

A*シンボル*関数またはコンパイルされたオブジェクト ファイルまたはライブラリによって内部的に使用するグローバル変数の名前を指定します。 シンボルは*定義*関数本体のコンパイル済みコードを配置する場所のグローバル変数、または関数の場合、記憶域が割り当てられているオブジェクト ファイルにします。 *外部シンボル*記号の*参照*は、使用、または 1 つのオブジェクトのファイルと呼ばれる、別のライブラリまたはオブジェクト ファイルで定義されています。 *エクスポートされたシンボル*オブジェクト ファイルまたはそれを定義するライブラリによって公開されている利用可能にする 1 つです。 リンカーである必要があります*解決*、または一致するアプリケーションまたは DLL にリンクされている場合は、オブジェクト ファイルによって参照されるすべての外部シンボルの定義を検索します。 リンク ファイルのいずれかで一致するエクスポートされたシンボルを検索して、外部シンボルを解決できない場合、リンカーはエラーを生成します。

## <a name="use-the-decorated-name-to-find-the-error"></a>装飾名を使用して、エラーを検索するには

C++ コンパイラとリンカーの使用[名前の装飾](../../error-messages/tool-errors/name-decoration.md)とも呼ばれる、*名前マングル*変数の型または戻り値の型、パラメーターの型、スコープ、および呼び出し元に関する追加情報をエンコードするにはシンボル名の関数の規則。 この装飾名は、外部シンボルを解決するのには、リンカーが検索シンボルの名前です。

追加情報では、シンボル名の一部になる、ために、関数または変数の宣言が関数または変数の定義と一致しない場合にリンク エラーが発生することができます。 これは、ソース ファイルをコンパイルするときに、異なるコンパイラ フラグを使用する場合、同じヘッダー ファイルが呼び出し元のコードと定義のコードの両方で使用される場合でもに発生することができます。 使用するコードがコンパイルされている場合にこのエラーが発生できるなど、`__vectorcall`が呼び出し元の規則は、既定値を使用して呼び出すクライアントが必要とするライブラリにリンク`__cdecl`または`__fastcall`呼び出し規約。 この場合、シンボル、一致しない呼び出し規約が異なるためです。

この種のエラーの原因を発見するために、リンカーのエラー メッセージ名を表示両方"フレンドリ、"ソース コード、および未解決の外部シンボルの装飾名を (かっこ内) で使用される名前。 その他の装飾名と比較することができる、装飾名を変換する方法を理解する必要はありません。 期待される記号名と実際のシンボル名の比較にコンパイラに含まれているコマンド ライン ツールを使用できます。

- [/Exports](../../build/reference/dash-exports.md)と[/symbols](../../build/reference/symbols.md) DUMPBIN コマンド ライン ツールのオプションを使用して、.dll、オブジェクトまたはライブラリ ファイルでシンボルが定義されているかを検出できます。 これを使用すると、エクスポートされた装飾する装飾名、リンカー検索の名前が一致を確認します。

場合によっては、リンカーはシンボルの装飾の名前のみを報告できます。 UNDNAME コマンド ライン ツールを使用して、装飾名の非装飾形式を取得することができます。

## <a name="additional-resources"></a>その他の技術情報

LNK2001 の考えられる原因および解決方法に関する詳細については、Stack Overflow の質問を参照してください。 [、未定義の参照/未解決外部シンボルというエラーと解決方法でしょうか。](http://stackoverflow.com/q/12573816/2002113)します。

