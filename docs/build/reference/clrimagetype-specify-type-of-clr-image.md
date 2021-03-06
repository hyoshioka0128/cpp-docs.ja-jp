---
title: /CLRIMAGETYPE (CLR イメージのタイプの指定)
ms.date: 11/04/2016
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
ms.openlocfilehash: c4cdb9a9ac3376762d6aa40fd4c13abbdc7b5487
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461634"
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE (CLR イメージのタイプの指定)

リンクの画像では、CLR イメージの種類を設定します。

## <a name="syntax"></a>構文

> **/CLRIMAGETYPE:**{**IJW**|**純粋**|**セーフ**|**は SAFE32BITPREFERRED**}

## <a name="remarks"></a>Remarks

リンカーは、ネイティブ オブジェクトを受け入れるし、MSIL オブジェクトを使用してコンパイルされたも[/clr](../../build/reference/clr-common-language-runtime-compilation.md)します。 **/Clr: 純粋な**と **/clr:safe**コンパイラ オプションは、Visual Studio 2015 で非推奨とされたおよび Visual Studio 2017 ではサポートされていません。 同じビルドに混在するオブジェクトを渡すと、生成される出力ファイルの検証可能性は、既定で入力モジュールの最低レベルの検証可能性と等しくなります。 たとえば、ネイティブ イメージと混合モード イメージを渡す場合 (を使用してコンパイル **/clr**)、結果のイメージは混合モード イメージになります。

使用することができます **/CLRIMAGETYPE**必要がある場合、検証可能性の低いレベルを指定します。

ファイルの CLR イメージのタイプを判断する方法については、「 [/CLRHEADER](../../build/reference/clrheader.md)」を参照してください。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクトのプロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. **[構成プロパティ]** ノードを展開します。

1. 展開、**リンカー**ノード。

1. 選択、**詳細**プロパティ ページ。

1. 変更、 **CLR イメージ タイプ**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

1. 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>

## <a name="see-also"></a>関連項目

- [リンカー オプションの設定](../../build/reference/setting-linker-options.md)
- [リンカー オプション](../../build/reference/linker-options.md)
