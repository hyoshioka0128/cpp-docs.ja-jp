---
title: /LIBPATH (追加ライブラリのパス)
ms.date: 11/04/2016
f1_keywords:
- /libpath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
helpviewer_keywords:
- LIBPATH linker option
- /LIBPATH linker option
- Additional Libpath linker option
- environment library path override
- -LIBPATH linker option
- library path linker option
ms.assetid: 7240af0b-9a3d-4d53-8169-2a92cd6958ba
ms.openlocfilehash: 40662e77faf03de8e5ef0abf334f4ec7be69c3ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615151"
---
# <a name="libpath-additional-libpath"></a>/LIBPATH (追加ライブラリのパス)

```
/LIBPATH:dir
```

## <a name="parameters"></a>パラメーター

*dir*<br/>
パスを指定します、LIB 環境オプションで指定されたパスを検索する前に、リンカーが検索します。

## <a name="remarks"></a>Remarks

/LIBPATH オプションを使用すると、環境ライブラリ パスをオーバーライドします。 リンカーはまず、このオプションで指定されたパスで検索し、LIB 環境変数で指定されたパスで検索します。 1 つだけのディレクトリを入力する各/LIBPATH オプションを指定できます。 1 つ以上のディレクトリを指定する場合は、複数の/LIBPATH オプションを指定する必要があります。 リンカーの順序で指定されたディレクトリが検索されます。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual c プロジェクトのプロパティの設定](../../ide/working-with-project-properties.md)します。

1. をクリックして、**リンカー**フォルダー。

1. をクリックして、**全般**プロパティ ページ。

1. 変更、**追加のライブラリ ディレクトリ**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalLibraryDirectories%2A>

## <a name="see-also"></a>関連項目

[リンカー オプションの設定](../../build/reference/setting-linker-options.md)<br/>
[リンカー オプション](../../build/reference/linker-options.md)