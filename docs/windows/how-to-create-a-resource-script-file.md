---
title: '方法: リソース スクリプト ファイル (C++) の作成'
ms.date: 11/04/2016
helpviewer_keywords:
- rc files [C++], creating
- .rc files [C++], creating
- resource script files [C++], creating
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
ms.openlocfilehash: eb884ca7520b34771c73e71c7ee9b4d811d5383c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491257"
---
# <a name="how-to-create-a-resource-script-file-c"></a>方法: リソース スクリプト ファイル (C++) の作成

> [!NOTE]
> **リソース エディター** Express エディションでは使用できません。
>
> これは Windows デスクトップ アプリケーションだけに適用できます。 .NET 言語のプロジェクトでは、リソース スクリプト ファイルを使用しません。 詳細については、「 [リソース ファイル (Visual Studio)](../windows/resource-files-visual-studio.md)」を参照してください。

### <a name="to-create-a-new-resource-script-rc-file"></a>リソース スクリプト (.rc) ファイルを新規作成するには

1. 既存のプロジェクト フォルダーにフォーカスを移す**ソリューション エクスプ ローラー**、たとえば、`MyProject`します。

   > [!NOTE]
   > ソリューション フォルダーを含むプロジェクトのフォルダーと混同しないでください**ソリューション エクスプ ローラー**します。 重点を置く場合、**ソリューション**フォルダーでの選択、**新しい項目の追加**ダイアログ ボックス (手順 3) では別になります。

2. **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。

3. **[新しい項目の追加]** ダイアログ ボックスで、 **[Visual C++]** フォルダーをクリックし、右側のペインの **[リソース ファイル (.rc)]** を選択します。

4. **[プロジェクト名]** ボックスにリソース スクリプト ファイルの名前を入力し、 **[開く]** をクリックします。

これで、新しいリソースを [作成](../windows/how-to-create-a-resource.md) して .rc ファイルに追加できます。

> [!NOTE]
> リソース スクリプト (.rc ファイル) を追加できるのは、Visual Studio IDE に読み込まれる既存のプロジェクトだけです。 プロジェクトの外側にあるスタンドアロンの .rc ファイルは作成できません。 [リソース テンプレート](../windows/how-to-use-resource-templates.md) (.rct ファイル) はいつでも作成できます。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[リソース ファイル](../windows/resource-files-visual-studio.md)<br/>
[リソース エディター](../windows/resource-editors.md)