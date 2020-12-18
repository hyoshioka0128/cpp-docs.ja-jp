---
description: '詳細情報: クラスを追加する'
title: クラスを追加する
ms.date: 05/14/2019
f1_keywords:
- vc.addclass
helpviewer_keywords:
- ATL projects, adding classes
- classes [C++], creating
- classes [C++], adding
- Add Class dialog box
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
ms.openlocfilehash: 71e4221b57a0a871d2c80396f4ac2261a4214fc9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160195"
---
# <a name="add-a-class"></a>クラスを追加する

Visual Studio C++ プロジェクトでクラスを追加するには、**ソリューション エクスプローラー** でプロジェクトを右クリックし、**[追加]**、**[クラス]** の順に選択します。 これで [[クラスの追加]](#add-class-dialog-box) ダイアログ ボックスが開きます。

クラスを追加するとき、MFC または ATL に既に存在するクラスのものとは異なる名前を指定する必要があります。 いずれかのライブラリに既に存在する名前を指定すると、IDE はエラー メッセージを表示します。

プロジェクト命名規則によって既存名の使用が要求される場合、名前の 1 つ以上の大文字を小文字に (あるいは小文字を大文字に) 変更できます。C++ では大文字と小文字が区別されるためです。 たとえば、クラスに `CDocument` という名前を付けることはできませんが、`cdocument` という名前を付けることができます。

## <a name="in-this-section"></a>このセクションの内容

- [追加するクラスの種類](#what-kind-of-class-do-you-want-to-add)
- [[クラスの追加] ダイアログ ボックス](#add-class-dialog-box)

## <a name="what-kind-of-class-do-you-want-to-add"></a>追加するクラスの種類

**[クラスの追加]** ダイアログ ボックスで、左のウィンドウの **[Visual C++]** ノードを展開すると、インストールされているテンプレートがいくつかのグループになって表示されます。 グループには、**CLR**、**ATL**、**MFC**、**C++** があります。 グループを選択すると、そのグループで利用できるテンプレートの一覧が真ん中のウィンドウに表示されます。 各テンプレートには、クラスに必要なファイルとソース コードが含まれています。

新しいクラスを生成するには、真ん中のウィンドウでテンプレートを選択し、**[名前]** ボックスにクラスの名前を入力し、**[追加]** を選択します。 **クラスの追加ウィザード** が開くので、クラスのオプションを指定できます。

- MFC クラスを作成する方法の詳細については、[MFC クラス](../mfc/reference/adding-an-mfc-class.md)に関するページを参照してください。

- ATL クラスを作成する方法の詳細については、[ATL シンプル オブジェクト](../atl/reference/adding-an-atl-simple-object.md)に関するページを参照してください。

> [!NOTE]
> **[MFC に ATL サポートを追加]** テンプレートの場合、クラスは作成されませんが、ATL を使用するようにプロジェクトが構成されます。 詳細については、[MFC プロジェクトの ATL サポート](../mfc/reference/adding-atl-support-to-your-mfc-project.md)に関するページを参照してください。

MFC、ATL、CLR を使用しない C++ クラスを作るには、インストールされているテンプレートの **C++** グループの **C++ クラス** テンプレートを使用します。 詳細については、「[一般 C++ クラスの追加](../ide/adding-a-generic-cpp-class.md)」を参照してください。

2 種類のフォームベース C++ クラスを利用できます。 最初の [CFormView クラス](../mfc/reference/cformview-class.md)では、MFC クラスが作成されます。 2 番目のクラスでは、CLR Windows フォーム クラスが作成されます。

## <a name="add-class-dialog-box"></a>[クラスの追加] ダイアログ ボックス

**[クラスの追加]** ダイアログ ボックスのテンプレートを使用すると、次の操作を実行できます。

- 対応するコード ウィザードを開始する (使用できる場合)。 詳細については、「[コード ウィザードを使用した機能の追加](../ide/adding-functionality-with-code-wizards-cpp.md)」を参照してください。

   \- または

- 適したファイルおよびソース コードをプロジェクトに追加して、新しいクラスを自動作成する。

**[クラスの追加]** ダイアログ ボックスには、**[プロジェクト]** メニュー、**ソリューション エクスプローラー**、[クラス ビュー](/visualstudio/ide/viewing-the-structure-of-code)からアクセスできます。

> [!NOTE]
> 現在のプロジェクトに対応しないクラスを追加しようとすると、エラー メッセージが表示されます。 **[OK]** を選択すると、**[クラスの追加]** ダイアログ ボックスに戻ります。

### <a name="add-class-templates"></a>クラスの追加テンプレート

**クラスの追加** テンプレートには、4 つのカテゴリ (.NET、ATL、MFC、汎用) があります。 **[テンプレート]** ウィンドウでテンプレートを選択すると、選択したテンプレートの説明が **[カテゴリ]** ウィンドウと **[テンプレート]** ウィンドウに表示されます。

#### <a name="net"></a>.NET

|Template|ウィザード|
|--------------|------------|
|ASP.NET Web サービス|使用不可|
|コンポーネント クラス (.NET)|使用不可|
|インストーラー クラス (.NET)|使用不可|
|ユーザー コントロール (.NET)|使用不可|
|Windows フォーム (.NET)|使用不可|

#### <a name="atl"></a>ATL

|Template|ウィザード|
|--------------|------------|
|MFC に ATL サポートを追加|使用不可|
|ATL コントロール|[ATL コントロール ウィザード](../atl/reference/atl-control-wizard.md)|
|ATL ダイアログ|[ATL ダイアログ ウィザード](../atl/reference/atl-dialog-wizard.md)|
|ATL シンプル オブジェクト|[ATL シンプル オブジェクト ウィザード](../atl/reference/atl-simple-object-wizard.md)|
|WMI イベント プロバイダー|WMI イベント プロバイダー ウィザード|
|WMI インスタンス プロバイダー|WMI インスタンス プロバイダー ウィザード|

#### <a name="mfc"></a>MFC

|Template|ウィザード|
|--------------|------------|
|MFC クラス|[MFC クラス追加ウィザード](../mfc/reference/mfc-add-class-wizard.md)|

#### <a name="generic-classes"></a>ジェネリック クラス

|Template|ウィザード|
|--------------|------------|
|汎用 C++ クラス|[汎用 C++ クラス ウィザード](./adding-a-generic-cpp-class.md#generic-c-class-wizard)|
