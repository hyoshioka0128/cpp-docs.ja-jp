---
title: /GR (ランタイム型情報の有効化)
ms.date: 11/04/2016
f1_keywords:
- /gr
- VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo
- VC.Project.VCCLCompilerTool.RuntimeTypeInfo
helpviewer_keywords:
- -Gr compiler option [C++]
- Gr compiler option [C++]
- RTTI compiler option
- /Gr compiler option [C++]
- enable run-time type information compiler option [C++]
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
ms.openlocfilehash: b0b618b1018912f1cf0172fc461ac2849c4faf5d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579349"
---
# <a name="gr-enable-run-time-type-information"></a>/GR (ランタイム型情報の有効化)

実行時にオブジェクトの種類をチェックするコードを追加します。

## <a name="syntax"></a>構文

```
/GR[-]
```

## <a name="remarks"></a>Remarks

ときに **/GR**に、コンパイラは、定義、`_CPPRTTI`プリプロセッサ マクロ。 既定では、 **/GR**にします。 **/GR-** 実行時の型情報を無効にします。

使用 **/GR**コンパイラがコード内のオブジェクトの種類を静的に解決できない場合。 通常は必要があります、 **/GR**コードで使用されるオプション[dynamic_cast Operator](../../cpp/dynamic-cast-operator.md)または[typeid](../../cpp/typeid-operator.md)します。 ただし、 **/GR** .rdata セクションでは、のイメージのサイズを大ききます。 コードを使用しない場合**dynamic_cast**または**typeid**、 **/GR-** 小さいイメージを生成する可能性があります。

実行時の型チェックの詳細については、次を参照してください。[実行時型情報](../../cpp/run-time-type-information.md)で、 *C++ 言語リファレンス*します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクトのプロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. **[C/C++]** フォルダーをクリックします。

1. をクリックして、**言語**プロパティ ページ。

1. 変更、**実行時型情報を有効にする**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A>

## <a name="see-also"></a>関連項目

[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)