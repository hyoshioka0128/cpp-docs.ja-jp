---
title: MFC クラス追加ウィザード
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.mfc.simple.overview
helpviewer_keywords:
- MFC Add Class Wizard
- wizards [MFC]
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
ms.openlocfilehash: 245963d4222188f16fd334d6950e04584ac1e978
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2018
ms.locfileid: "51520843"
---
# <a name="mfc-add-class-wizard"></a>MFC クラス追加ウィザード

このコード ウィザードを使用して、既存の MFC プロジェクトにクラスを追加するか、MFC をサポートする ATL プロジェクトにクラスを追加します。 MFC をサポートする Win32 プロジェクトに MFC クラスを追加することもできます。 プロジェクトの作成時に指定した機能は、このダイアログ ボックスで使用可能なオプションを決定します。

## <a name="names"></a>名前

このページで、クラス名、基底クラス、および新しいクラスのファイル名を指定します。

- **クラス名**

  新しいクラスの名前を指定し、Id とこのページ上のファイルの名前の既定の基盤を提供します。 たとえば、""が「が付きます」の C++ クラスは通常"C"で開始します。

- **基本クラス**

  新しいクラスの基底クラスの名前を指定します。 基本クラスは、既定では、 [CWnd](../../mfc/reference/cwnd-class.md)します。 選択した基本クラスは、このページの他のボックスがアクティブかどうかを判断します。

  基底クラスでは、ダイアログの ID またはリソース id。 クラスがあるかどうかを判断すると、設定するクラスの型 一般的な種類のクラスは次のとおりです。

  - などのクラス[CButton](../../mfc/reference/cbutton-class.md)、 [CWnd](../../mfc/reference/cwnd-class.md)、または[CDocument](../../mfc/reference/cdocument-class.md)、このダイアログ ボックスを必要としない ID またはリソース id です。 これらのクラスは、ダイアログまたはリソース ID を使用しません。 基底クラスのこれらのクラスのいずれかを選択した場合、**ダイアログ ID**ボックスおよび**DHTML のリソース ID**ボックスは淡色表示になります。

  - などのクラス[CDialog](../../mfc/reference/cdialog-class.md)、 [CFormView](../../mfc/reference/cformview-class.md)、または[CPropertyPage](../../mfc/reference/cpropertypage-class.md)ダイアログの id これが必要です。

  - クラスは、 [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)ダイアログの ID、DHTML のリソース ID、および HTML のファイル名を必要があります。

  ダイアログの ID を必要とすると、クラスの場合がありますを使用する方が効率的、[リソース エディター](../../windows/resource-editors.md)ダイアログ リソースを作成するには、その ID を割り当てる、[プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window)、し、関連するクラスを作成そのリソース ID に置き換えます。 参照してください[ ダイアログ ボックスの新規作成](../../windows/creating-a-new-dialog-box.md)標準 Windows ダイアログ ボックスの作成の詳細についてはします。

  > [!NOTE]
  > まずダイアログ リソースを作成してから、新しいクラスを派生させるかどうか`CDHtmlDialog`、標準の Windows を削除**OK**と**キャンセル**ボタン、[既定] ダイアログ ボックスに表示されます。 それ自体が含まれている DHTML フォームをホストする、標準の Windows ダイアログ ボックス**OK**と**キャンセル**ボタン。

  ダイアログ ボックスは、Windows コントロールと DHTML コントロールの両方に含めることができますは推奨されません。

- **ダイアログ ID**

  選択した場合、ダイアログの ID を指定します`CDialog`、 `CFormView`、 `CPropertyPage`、または`CDHtmlDialog`として、**基本クラス**します。

- **.h ファイル**

  新しいオブジェクトのクラスにヘッダー ファイルの名前を設定します。 既定では、この名前は、**[クラス名]** で指定した名前に基づきます。 選択した場所にファイル名を保存するには、あるいはクラス宣言を既存のファイルに追加するには、省略記号ボタンをクリックします。 既存のファイルを選択した場合、ウィザードで **[完了]** をクリックするまで、ファイルは選択した場所に保存されません。

  ウィザードではファイルは上書きされません。 既存のファイルの名前を選択する場合、**[完了]** をクリックすると、ウィザードからクラス宣言をファイルのコンテンツに追加するかどうかを指定するように求められます。 ファイルを追加するには、**[はい]** をクリックします。ウィザードに戻り、別のファイル名を指定するには、**[いいえ]** をクリックします。

- **.cpp ファイル**

  新しいオブジェクトのクラスに実装ファイルの名前を設定します。 既定では、この名前は、**[クラス名]** で指定した名前に基づきます。 ファイル名を選択した場所に保存するには、省略記号ボタンをクリックします。 ファイルは、ウィザードで **[完了]** をクリックするまで選択した場所に保存されません。

  ウィザードではファイルは上書きされません。 既存のファイルの名前を選択する場合、**[完了]** をクリックすると、ウィザードからクラスの実装をファイルのコンテンツに追加するかどうかを指定するように求められます。 ファイルを追加するには、**[はい]** をクリックします。ウィザードに戻り、別のファイル名を指定するには、**[いいえ]** をクリックします。

- **アクティブなユーザー補助機能**

  MFC の Active Accessibility のサポートを呼び出すことによって有効[EnableActiveAccessibility](../../mfc/reference/cwnd-class.md#enableactiveaccessibility)コンス トラクターでします。 派生したクラスのこのオプションは使用可能な[CWnd](../../mfc/reference/cwnd-class.md)します。

- **DHTML のリソース ID**

  派生したクラスに適用されます`CDHtmlDialog`のみです。 DHTML のダイアログ ボックスのリソース ID を指定します。 HTML ダイアログ ボックスのファイル名と共に、プロジェクトの .rc ファイルの HTML のセクションでは、リソース ID が表示されます。 DHTML リソースは、この ID によって識別がで識別される、ダイアログ ボックスでホストされている**ダイアログ ID**します。

- **.HTM ファイル**

  派生したクラスに適用されます`CDHtmlDialog`のみです。 DHTML のダイアログ ボックスの HTML ファイルの名前を設定します。 既定では、このファイル名は、クラス名に基づいています。 DHTML のダイアログ ボックスのリソース ID と共に、プロジェクトの .rc ファイルの HTML のセクションでは、ファイル名が表示されます。

- **オートメーション**

  クラスのサポートのレベルを設定[Automation](../../mfc/automation.md)します。 クラス レベルでオートメーションは、オートメーションをサポートするすべてのクラスを使用できます。 オートメーションのサポートで作成したプロジェクトの利用もできます。 つまり、いずれか、MFC プロジェクト[ATL サポート](../../atl/reference/mfc-support-in-atl-projects.md)、または MFC プロジェクトを選択した、 **Automation**  チェック ボックス、[高度な機能](../../mfc/reference/advanced-features-mfc-application-wizard.md)MFC のページアプリケーション ウィザードです。

  |オプション|説明|
  |------------|-----------------|
  |**None**|クラスにオートメーションのサポートが含まれていないことを示します。|
  |**オートメーション**|クラスがオートメーションをサポートしていることを示します。 このオプションを選択する場合は、新しく作成されたクラスは Microsoft Visual Basic や Microsoft Excel などのオートメーション クライアント アプリケーションによってプログラミング可能なオブジェクトとして使用可能なです。 このオプションは、この表の後に記載されている基本クラスのご利用いただけません。|
  |**タイプ ID で作成可能**|クラスとプロジェクトの両方がオートメーションを使用してこのクラスのオブジェクトを作成する他のアプリケーションをサポートすることを示します。 このオプションでは、オートメーション クライアントは、オートメーション オブジェクトを直接作成できます。 テキスト ボックスに、型 ID は; を作成するオブジェクトを指定するクライアント アプリケーションで使用します。システム全体と、一意である必要があります。 このオプションは、この表の後に記載されている基本クラスのご利用いただけません。|

  オートメーションのサポートでは、次の基本クラスを使用できません。

  - `CAsyncMonitorFile`

  - `CAsyncSocket`

  - `CCachedDataPathProperty`

  - `CConnectionPoint`

  - `CDatabase`

  - `CDataPathProperty`

  - `CHttpFilter`

  - `CHttpServer`

  - `CInternetSession`

  - `CObject`

  - `CSocket`

- **種類 ID**

  クラスの型 ID を設定します。 **タイプ ID**ボックスには、次のようにするプロジェクト名と新しいクラスの名前が連結: *MFCProj.MFCClass*します。 この ID は、選択した場合にのみ変更可能な**Automation**オプション**タイプ ID で Creatable**します。

- **ドキュメント テンプレート リソースを生成します。**

  アプリケーションによって作成されたドキュメントのドキュメント テンプレートのリソースであることを示します。 このチェック ボックスをアクティブ化するプロジェクトが MFC のドキュメント/ビュー アーキテクチャをサポートし、このクラスの基底クラスである必要があります[CFormView](../../mfc/reference/cformview-class.md)します。

  参照してください[ドキュメント テンプレートとドキュメント/ビューの作成手順](../../mfc/document-templates-and-the-document-view-creation-process.md)詳細についてはします。

## <a name="see-also"></a>関連項目

[MFC クラス](../../mfc/reference/adding-an-mfc-class.md)<br/>
[クラスの追加](../../ide/adding-a-class-visual-cpp.md)
