---
title: /FC (診断時のソース コード ファイルの完全パス)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UseFullPaths
- /FC
helpviewer_keywords:
- /FC compiler option [C++]
- -FC compiler option [C++]
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
ms.openlocfilehash: 3629ec35f0be5ebfd384b949acb2910dcbea3318
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624914"
---
# <a name="fc-full-path-of-source-code-file-in-diagnostics"></a>/FC (診断時のソース コード ファイルの完全パス)

コンパイラ診断でコンパイラに渡されるソース コード ファイルの完全なパスを表示します。

## <a name="syntax"></a>構文

> /FC

## <a name="remarks"></a>Remarks

次のコード サンプルを検討してください。

```cpp
// compiler_option_FC.cpp
int main( ) {
   int i   // C2143
}
```

せず **/FC**、診断用のテキストはこの診断用のテキストのようになります。

- compiler_option_FC.cpp(5): エラー C2143: 構文エラー: 不足している ';' は、前に '}'

**/FC**、診断用のテキストはこの診断用のテキストのようになります。

- c:\test\compiler_option_fc.cpp(5): エラー C2143: 構文エラー: 不足している ';' は、前に '}'

**/FC**を使用する場合は、ファイル名の完全なパスを表示する場合にも必要です、 &#95;&#95;ファイル&#95;&#95;マクロ。 参照してください[定義済みマクロ](../../preprocessor/predefined-macros.md)の詳細については&#95;&#95;ファイル&#95;&#95;します。

**/FC**がオプションが含まれる **/ZI**します。 詳細については **/ZI**を参照してください[/Z7、/Zi、/ZI (デバッグ情報の形式)](../../build/reference/z7-zi-zi-debug-information-format.md)します。

**/FC**小文字で完全なパスを出力します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクトのプロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. 選択、**構成プロパティ** > **C/C++** > **詳細**プロパティ ページ。

1. 変更、**完全パスの使用**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>

## <a name="see-also"></a>関連項目

[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)
