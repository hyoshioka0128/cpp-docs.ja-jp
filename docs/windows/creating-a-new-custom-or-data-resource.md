---
title: 新しいカスタム リソースまたはデータ リソース (C++) を作成します。
ms.date: 11/04/2016
f1_keywords:
- vc.editors.binary
helpviewer_keywords:
- custom resources [C++]
- data resources [C++]
- resources [C++], creating
ms.assetid: 9918bf96-38fa-43a1-a384-572f95d84950
ms.openlocfilehash: 7b4044921a26e572c53e1a070611c78323d3ca1e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590477"
---
# <a name="creating-a-new-custom-or-data-resource-c"></a>新しいカスタム リソースまたはデータ リソース (C++) を作成します。

プロジェクトを右クリックして通常のリソース スクリプト (.rc) ファイルの構文を使用して別のファイルに、そのファイルをインクルードし、リソースを配置して、新しいカスタム リソースやデータ リソースを作成する**ソリューション エクスプ ローラー** ]をクリック**リソースが含まれます**ショートカット メニューの [します。

### <a name="to-create-a-new-custom-or-data-resource"></a>新しいカスタム リソースやデータ リソースを作成するには

1. カスタム リソースやデータ リソースが格納される[.rc ファイルを作成します](../windows/how-to-create-a-resource-script-file.md) 。

   null で終わる引用符で囲まれた文字列として、または 10 進数、16 進数、または 8 進数形式の整数として.rc ファイルにカスタム データを入力することができます。

2. **ソリューション エクスプローラー**でプロジェクトの .rc ファイルを右クリックし、ショートカット メニューの **[リソース ファイルのインクルード]** をクリックします。

3. **コンパイル時ディレクティブ**ボックスに、入力、`#include`カスタム リソースを含むファイルの名前を指定するステートメント。 例えば:

    ```cpp
    #include mydata.rc
    ```

   入力する構文とスペルが正しいことを確認します。 **[コンパイル時に追加するファイル]** ボックスの内容が、入力したとおりにリソース スクリプト ファイルに挿入されます。

4. **[OK]** をクリックして変更を記録します。

カスタム リソースを作成する別の方法として、外部ファイルをカスタム リソースとしてインポートする方法もあります。 詳細については、「 [リソースのインポートとエクスポート](../windows/how-to-import-and-export-resources.md)」を参照してください。

マネージ プロジェクトにリソースを追加する方法についてを参照してください[Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[Binary Editor](binary-editor.md)