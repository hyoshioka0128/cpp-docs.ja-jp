---
title: /Yd (デバッグ情報のオブジェクト ファイルへの取り込み)
ms.date: 11/04/2016
f1_keywords:
- /yd
helpviewer_keywords:
- /Yd compiler option [C++]
- -Yd compiler option [C++]
- debugging [C++], debug information files
- Yd compiler option [C++]
ms.assetid: c5a699fe-65ce-461e-964c-7f5eb2a8320a
ms.openlocfilehash: eda3dd38449f89d9b8d767b460970d659f6c9dc9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430018"
---
# <a name="yd-place-debug-information-in-object-file"></a>/Yd (デバッグ情報のオブジェクト ファイルへの取り込み)

使用する場合は、プリコンパイル済みヘッダー (.pch) ファイルから作成されるデバッグ情報をすべてのオブジェクト ファイルの完全な性能を試します、 [/Yc](../../build/reference/yc-create-precompiled-header-file.md)と[/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)オプション。 非推奨。

## <a name="syntax"></a>構文

```
/Yd
```

## <a name="remarks"></a>Remarks

**/Yd への取り込み**は非推奨とされます。Visual C では、複数のオブジェクトが 1 つの .pdb ファイルへの書き込みをサポートを使用して **/Zi**代わりにします。 非推奨のコンパイラ オプションの一覧は、次を参照してください。**非推奨とされた削除済みのコンパイラ オプション**で[Compiler Options Listed by Category](../../build/reference/compiler-options-listed-by-category.md)します。

使用して、デバッグ情報を含むライブラリを配布する必要がない限り、 [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)オプションなく **/Z7**と **/yd への取り込み**します。

すべての .obj ファイルに詳細なデバッグ情報を格納するは、デバッグ情報が含まれているライブラリを配布する場合にのみ必要があります。 これにより、コンパイル速度が低下し、かなりのディスク領域が必要です。 ときに **/Yc**と **/Z7**されずに使用されます **/yd への取り込み**コンパイラが .pch ファイルから作成された最初の .obj ファイル内の一般的なデバッグ情報を格納します。 コンパイラが .obj ファイルの .pch ファイルから作成された後にこの情報を挿入できません。相互参照情報を挿入します。 .Obj ファイルの数は、.pch ファイルを使用して、関係なく 1 つだけの .obj ファイルには、一般的なデバッグ情報が含まれています。

この既定の動作の結果は、ビルド時間が高速化、ディスク領域の負担を軽減、これは望ましくありませんわずかな変更は、一般的なデバッグ情報を含む .obj ファイルを再構築が必要な場合。 この場合、コンパイラには、.obj ファイルへの相互参照を含むすべての .obj ファイルが再構築する必要があります。 また、異なるプロジェクトで共通の .pch ファイルを使用する場合の相互参照を 1 つの .obj ファイルへの依存は困難です。

プリコンパイル済みヘッダーの詳細についてを参照してください。

- [/Y (プリコンパイル済みヘッダー)](../../build/reference/y-precompiled-headers.md)

- [プリコンパイル済みヘッダー ファイルの作成](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクトのプロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. **[C/C++]** フォルダーをクリックします。

1. **[コマンド ライン]** プロパティ ページをクリックします。

1. **[追加のオプション]** ボックスにコンパイラ オプションを入力します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="examples"></a>使用例

F.cpp とこれらの各を格納している G.cpp 2 つの基本ファイルがあるとします **#include**ステートメント。

```
#include "windows.h"
#include "etc.h"
```

次のコマンドは、プリコンパイル済みヘッダーを作成します。 ファイル ETC.pch と F.obj オブジェクト ファイル。

```
CL /YcETC.H /Z7 F.CPP
```

F.obj オブジェクト ファイルには、型と WINDOWS.h および ETC.h のシンボル情報 (および他のヘッダー ファイルが含まれている) が含まれています。 今すぐ G.cpp ソース ファイルをコンパイルするのに ETC.pch プリコンパイル済みヘッダーを使用できます。

```
CL /YuETC.H /Z7 G.CPP
```

G.obj オブジェクト ファイルでは、プリコンパイル済みヘッダーのデバッグ情報は含まれませんが、単に F.obj ファイルでは、その情報を参照します。 F.obj とリンクする必要があることに注意してください。

プリコンパイル済みヘッダーでコンパイルされて場合 **/Z7**、以降のコンパイルを使用してそのまま使用することができます **/Z7**します。 ただし、デバッグ情報が現在のオブジェクト ファイル内に配置して、関数と、プリコンパイル済みヘッダーで定義された型のローカル シンボルは、デバッガーを使用できません。

## <a name="see-also"></a>関連項目

[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)