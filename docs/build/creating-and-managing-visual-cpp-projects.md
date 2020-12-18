---
description: '詳細情報: Visual Studio のプロジェクト - C++'
title: Visual Studio のプロジェクト - C++
ms.date: 10/25/2019
helpviewer_keywords:
- ATL projects, creating
- Visual Studio C++ projects, creating
- projects [C++], creating
- Visual Studio C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
ms.openlocfilehash: 07c7c0394c7b1a49bd4b8861540e540b095fae5a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156815"
---
# <a name="visual-studio-projects---c"></a>Visual Studio のプロジェクト - C++

"*Visual Studio のプロジェクト*" は、MSBuild のビルド システムに基づくプロジェクトです。 MSBuild は、Visual Studio のネイティブ ビルド システムであり、通常は Windows 固有のプログラムで使用するための最適なビルド システムです。 MSBuild は Visual Studio と緊密に統合されていますが、コマンド ラインから使うこともできます。 クロスプラットフォーム プロジェクト、またはオープンソース ライブラリを使用するプロジェクトでは、Visual Studio 2017 以降で [Visual Studio の CMake プロジェクト](cmake-projects-in-visual-studio.md)を使用することをお勧めします。 以前のバージョンの Visual Studio から MSBuild プロジェクトをアップグレードする方法の詳細については、「[Microsoft C++ 移植およびアップグレード ガイド](../porting/visual-cpp-porting-and-upgrading-guide.md)」を参照してください。

## <a name="create-a-project"></a>プロジェクトを作成する

::: moniker range="msvc-160"

C++ プロジェクトを作成するには、 **[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択し、 **[言語]** を C++ に設定します。 結果の一覧に表示されるプロジェクト テンプレートのリストは、 **[プラットフォーム]** または **[プロジェクトの種類]** を設定し、検索ボックスにキーワードを入力することで、フィルター処理できます。

   ![Visual Studio 2019 プロジェクト テンプレート](../build/media/vs2019-choose-console-app.png "Visual Studio 2019 の [新しいプロジェクト] ダイアログ")

::: moniker-end

::: moniker range="msvc-150"

C++ プロジェクトを作成するには、 **[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択し、左側のウィンドウで Visual C++ を選択します。 中央のウィンドウに、プロジェクト テンプレートの一覧が表示されます。

   ![プロジェクト テンプレート](../overview/media/vs2017-new-project.png "Visual Studio 2017 の [新しいプロジェクト] ダイアログ")

::: moniker-end

Visual Studio に含まれるすべての既定のプロジェクト テンプレートについて詳しくは、[Visual Studio での C++ プロジェクト テンプレート](reference/visual-cpp-project-types.md) に関する記事をご覧ください。 独自のプロジェクト テンプレートを作成することができます。 詳細については、[プロジェクト テンプレートを作成する](/visualstudio/ide/how-to-create-project-templates)」をご覧ください。

作成したプロジェクトは、[[ソリューション エクスプローラー]](/visualstudio/ide/solutions-and-projects-in-visual-studio) ウィンドウに表示されます。

   ![ソリューション エクスプローラー](media/mathlibrary-solution-explorer-153.png)

新しいプロジェクトを作成すると、ソリューション ファイル (.sln) も作成されます。 **ソリューション エクスプローラー** でソリューションを右クリックして、ソリューションに他のプロジェクトを追加できます。 ソリューション ファイルは、複数の関連プロジェクトがあるときにビルドの依存関係を調整するために使われますが、それ以外のことには使われません。 すべてのコンパイラ オプションは、プロジェクト レベルで設定されます。

## <a name="add-items"></a>項目を追加する

ソース コード ファイル、アイコン、その他の項目をプロジェクトに追加するには、**ソリューション エクスプローラー** でプロジェクトを右クリックして、 **[追加] > [新規]** または **[追加] > [既存]** を選択します。

## <a name="add-third-party-libraries"></a>サード パーティ製のライブラリを追加する

サードパーティ製のライブラリを追加するには、[vcpkg](vcpkg.md) パッケージ マネージャーを使います。 Visual Studio プロジェクトからライブラリを参照するときに、Visual Studio 統合手順を実行して、そのライブラリへのパスを設定します。

## <a name="set-compiler-options-and-other-build-properties"></a>コンパイラ オプションおよび他のビルド プロパティを設定する

プロジェクトのビルド設定を構成するには、**ソリューション エクスプローラー** でプロジェクトを右クリックして、 **[プロパティ]** を選択します。 詳しくは、「[Visual Studio で C++ コンパイラとビルド プロパティを設定する](working-with-project-properties.md)」をご覧ください。

## <a name="compile-and-run"></a>コンパイルして実行する

新しいプロジェクトをコンパイルして実行するには、**F5** キーを押すか、またはメイン ツールバーの緑色の矢印が付いた "*デバッグ ドロップダウン*" をクリックします。 "*構成ドロップダウン*" では、"*デバッグ*" ビルドまたは "*リリース*" ビルド (または他のカスタム構成) を実行するかどうかを選択します。

新しいプロジェクトがエラーなしでコンパイルされます。 独自のコードを追加すると、エラーが発生したり、警告がトリガーされたりする場合があります。 エラーがあるとビルドは完了しませんが、警告では完了します。 プロジェクトをビルドするとき、すべてのエラーと警告は出力ウィンドウとエラー一覧の両方に表示されます。

   ![出力ウィンドウとエラー一覧](../overview/media/vs2017-output-error-list.png)

エラー一覧では、強調表示されているエラーで **F1** キーを押して、そのドキュメント トピックに移動できます。

## <a name="in-this-section"></a>このセクションの内容

[Visual Studio で C++ コンパイラとビルド プロパティを設定する](working-with-project-properties.md)<br/>
プロパティ ページおよびプロパティ シートを使って、プロジェクトの設定を指定する方法。

[ビルド時にライブラリとコンポーネントを参照する](adding-references-in-visual-cpp-projects.md)<br/>
プロジェクトにライブラリ、DLL、COM、.NET コンポーネントを組み込む方法。

[プロジェクト出力ファイルを編成する](how-to-organize-project-output-files-for-builds.md)<br/>
ビルド プロセスで作成される実行可能ファイルの場所をカスタマイズする方法。

[カスタム ビルド ステップとビルド イベント](understanding-custom-build-steps-and-build-events.md)<br/>
ビルド プロセスの指定したポイントに任意のコマンドを追加する方法。

[既存のコードからプロジェクトを作成する](how-to-create-a-cpp-project-from-existing-code.md)<br/>
ソース ファイルの緩やかなコレクションから新しい Visual Studio プロジェクトを作成する方法。

## <a name="see-also"></a>関連項目

[プロジェクトおよびビルド システム](projects-and-build-systems-cpp.md)<br>
[Visual C++ 移植およびアップグレード ガイド](../porting/visual-cpp-porting-and-upgrading-guide.md)
