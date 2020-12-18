---
description: '詳細情報: ビルド イベントの指定'
title: ビルド イベントの指定
ms.date: 12/28/2017
f1_keywords:
- VC.Project.IVCEventTool.CommandLine
- VC.Project.IVCEventTool.ExcludedFromBuild
- VC.Project.IVCEventTool.Description
helpviewer_keywords:
- Pre-Link event
- build events [C++], specifying
- custom build steps [C++], build events
- builds [C++], events
- events [C++], build
- builds [C++], customizing C++
- build events [C++]
- post-build events
ms.assetid: 788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc
ms.openlocfilehash: 1d1dc9a1f0e379c3abe36117beaf9ef58bcbd064
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275400"
---
# <a name="specifying-build-events"></a>ビルド イベントの指定

ビルド開始前、リンク プロセス前、ビルド終了後に実行するコマンドを指定する目的で、ビルド イベントを使用できます。

ビルド イベントは、ビルド プロセスにおいてビルドがこれらのポイントに正常に達した場合にのみ実行されます。 ビルドでエラーが発生した場合、*ビルド後* イベントは発生しません。リンク段階前にエラーが発生した場合、*リンク前* イベントも *ビルド後* イベントも発生しません。 また、ファイルをリンクする必要がない場合、*リンク前* イベントは発生しません。 リンク手順が含まれないプロジェクトでも、*リンク前* イベントを利用できません。

ファイルをビルドする必要がない場合、ビルド イベントは発生しません。

ビルド イベントに関する全般情報については、「[カスタム ビルド ステップとビルド イベントについて](understanding-custom-build-steps-and-build-events.md)」を参照してください。

### <a name="to-specify-a-build-event"></a>ビルド イベントを指定するには

1. **ソリューション エクスプローラー** で、ビルド イベントを指定するプロジェクトを選択します。

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳しくは、「[Visual Studio で C++ コンパイラとビルド プロパティを設定する](working-with-project-properties.md)」をご覧ください。

1. **[ビルド イベント]** フォルダーで、ビルド イベント プロパティ ページを選択します。

1. ビルド イベントに関連付けられたプロパティを指定します。

   - **[コマンド ライン]** で、コマンド プロンプトの場合と同様にコマンドを指定します。 有効なコマンドまたはバッチ ファイルと必要な入力ファイルまたは出力ファイルがあればそれを指定します。 後続のコマンドがすべて確実に実行されるように、バッチ ファイル名の前に **call** バッチ コマンドを指定します。

      MSBuild マクロを利用すれば、複数の入力ファイルと出力ファイルを数式で指定できます。 ファイルの場所またはファイル セットの名前を指定する方法については、[ビルドのコマンドとプロパティの共通マクロ](reference/common-macros-for-build-commands-and-properties.md)に関するページを参照してください。

      '%' は MSBuild に予約されている文字です。環境変数を指定する場合、エスケープ文字 **%** をそれぞれ、16 進数エスケープ シーケンス **%25** に変更してください。 たとえば、 **%WINDIR%** を **%25WINDIR%25** に変更します。 MSBuild は **%25** シーケンスをそれぞれ **%** 文字に変更し、それから環境変数にアクセスします。

   - **[説明]** には、このイベントの説明を入力します。 このイベントが発生したとき、 **[出力]** ウィンドウにこの説明が表示されます。

   - **[ビルドから除外]** には、イベントを実行しない場合、 **[はい]** を指定します。

## <a name="see-also"></a>関連項目

[カスタム ビルド ステップとビルド イベントについて](understanding-custom-build-steps-and-build-events.md)<br>
[ビルドのコマンドとプロパティの共通マクロ](reference/common-macros-for-build-commands-and-properties.md)<br>
[ビルドのカスタマイズのトラブルシューティング](troubleshooting-build-customizations.md)
