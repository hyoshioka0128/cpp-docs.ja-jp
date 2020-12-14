---
description: '詳細については、「MFC ActiveX コントロール: 高度なトピック」を参照してください。'
title: 'MFC ActiveX コントロール : 高度なトピック'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- MFC ActiveX controls [MFC], accessing invisible dialog controls
- MFC ActiveX controls [MFC], advanced topics
- FireError method [MFC]
- MFC ActiveX controls [MFC], database classes
- MFC ActiveX controls [MFC], special keys
- PreTranslateMessage method [MFC]
- MFC ActiveX controls [MFC], parameterized property
- ThrowError method [MFC]
ms.assetid: e9e34abb-8e2d-461e-bb9c-a1aec5dcecbd
ms.openlocfilehash: 1b37c3621c515153f068633b8272420a68a06c4e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280743"
---
# <a name="mfc-activex-controls-advanced-topics"></a>MFC ActiveX コントロール : 高度なトピック

この記事では、ActiveX コントロールの開発に関連する高度なトピックについて説明します。 これには以下が含まれます。

- [ActiveX コントロールでのデータベースクラスの使用](#_core_using_database_classes_in_activex_controls)

- [パラメーター化されたプロパティの実装](#_core_implementing_a_parameterized_property)

- [ActiveX コントロールでのエラーの処理](#_core_handling_errors_in_your_activex_control)

- [コントロールでの特殊なキーの処理](#_core_handling_special_keys_in_your_control)

- [実行時に非表示になるダイアログコントロールへのアクセス](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)

>[!IMPORTANT]
> ActiveX は、新しい開発には使用しない従来のテクノロジです。 ActiveX を置き換える最新テクノロジの詳細については、「 [Activex コントロール](activex-controls.md)」を参照してください。

## <a name="using-database-classes-in-activex-controls"></a><a name="_core_using_database_classes_in_activex_controls"></a> ActiveX コントロールでのデータベースクラスの使用

ActiveX コントロールクラスはクラスライブラリの一部であるため、標準の MFC アプリケーションでデータベースクラスを使用する場合と同じ手順と規則を適用して、MFC データベースクラスを使用する ActiveX コントロールを開発できます。

MFC データベースクラスの一般的な概要については、「 [Mfc データベースクラス (DAO および ODBC)](../data/mfc-database-classes-odbc-and-dao.md)」を参照してください。 この記事では、MFC ODBC クラスと MFC DAO クラスの両方について説明します。詳細については、こちらを参照してください。

> [!NOTE]
> DAO は Office 2013 でサポートされています。 DAO 3.6 は最終バージョンであり、互換性のために残されているものと見なされます。 Visual C++ 環境とウィザードでは、DAO はサポートされていません (ただし、DAO クラスは含まれていますが、引き続き使用できます)。 新しいプロジェクトには、 [OLE DB テンプレート](../data/oledb/ole-db-programming.md) または [ODBC および MFC](../data/odbc/odbc-and-mfc.md) を使用することをお勧めします。 既存のアプリケーションを維持するには、DAO のみを使用する必要があります。

## <a name="implementing-a-parameterized-property"></a><a name="_core_implementing_a_parameterized_property"></a> パラメーター化されたプロパティの実装

パラメーター化されたプロパティ (プロパティ配列とも呼ばれます) は、同種の値のコレクションをコントロールの単一のプロパティとして公開するためのメソッドです。 たとえば、パラメーター化されたプロパティを使用して、配列またはディクショナリをプロパティとして公開できます。 Visual Basic では、このようなプロパティには配列表記を使用してアクセスします。

[!code-vb[NVC_MFC_AxVb#1](codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]

パラメーター化されたプロパティを実装するには、プロパティの追加ウィザードを使用します。 プロパティの追加ウィザードでは、Get/Set 関数のペアを追加することによってプロパティを実装します。これにより、コントロールユーザーは、上記の表記法または標準の方法を使用してプロパティにアクセスできるようになります。

パラメーター化されたプロパティには、メソッドやプロパティと同様に、許可されるパラメーターの数も制限されます。 パラメーター化されたプロパティの場合、制限は15個のパラメーターです (プロパティ値を格納するために1つのパラメーターが予約されています)。

次の手順では、配列と呼ばれるパラメーター化されたプロパティを追加します。このプロパティには、整数の2次元配列としてアクセスできます。

#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>プロパティの追加ウィザードを使用してパラメーター化されたプロパティを追加するには

1. コントロールのプロジェクトを読み込みます。

1. [クラス ビュー] で、コントロールのライブラリ ノードを展開します。

1. コントロールのインターフェイス ノード (ライブラリ ノードの 2 番目のノード) を右クリックし、ショートカット メニューを開きます。

1. ショートカットメニューの [ **追加** ] をクリックし、[ **プロパティの追加**] をクリックします。

1. [ **プロパティ名** ] ボックスに「」と入力 `Array` します。

1. [ **プロパティの種類** ] ボックスで、を選択し **`short`** ます。

1. [ **実装** の種類] で、[ **Get/Set メソッド**] をクリックします。

1. **Get 関数** と **set 関数** の各ボックスに、Get 関数と set 関数に一意の名前を入力するか、既定の名前をそのまま使用します。

1. パラメーター **名** と **パラメーターの型** コントロールを使用して、*行*(型 *short*) と呼ばれるパラメーターを追加します。

1. *列*( *short* 型) という2番目のパラメーターを追加します。

1. **[完了]** をクリックします。

### <a name="changes-made-by-the-add-property-wizard"></a>プロパティの追加ウィザードによって行われた変更

カスタムプロパティを追加すると、プロパティの追加ウィザードによってコントロールクラスヘッダー () が変更されます。H) と実装 (.CPP) ファイル。

次の行がコントロールクラスに追加されます。H ファイル:

[!code-cpp[NVC_MFC_AxUI#35](codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]

このコードは、という2つの関数を宣言 `GetArray` し `SetArray` ます。これにより、ユーザーは、プロパティにアクセスするときに特定の行と列を要求できるようになります。

さらに、プロパティの追加ウィザードでは、コントロールクラスの実装 () にあるコントロールのディスパッチマップに次の行を追加します。CPP) ファイル:

[!code-cpp[NVC_MFC_AxUI#36](codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]

最後に、 `GetArray` 関数と関数の実装 `SetArray` がの末尾に追加されます。CPP ファイル。 ほとんどの場合、プロパティの値を返すように Get 関数を変更します。 Set 関数には、通常、プロパティが変更される前または後に実行する必要があるコードが含まれます。

このプロパティを使用するには、パラメーター化された **`short`** プロパティの値を格納するために、型のコントロールクラスで2次元配列のメンバー変数を宣言します。 次に、パラメーターで示されているように、適切な行と列に格納されている値を返すように Get 関数を変更し、行と列のパラメーターによって参照される値を更新するように Set 関数を変更します。

## <a name="handling-errors-in-your-activex-control"></a><a name="_core_handling_errors_in_your_activex_control"></a> ActiveX コントロールでのエラーの処理

コントロールでエラー状態が発生した場合は、コントロールコンテナーにエラーを報告することが必要になる場合があります。 エラーを報告するには、エラーが発生した状況に応じて2つの方法があります。 プロパティの Get または Set 関数内、または OLE オートメーションメソッドの実装内でエラーが発生した場合、コントロールは、エラーが発生したことをコントロールユーザーに通知する、 [COleControl:: ThrowError](reference/colecontrol-class.md#throwerror)を呼び出す必要があります。 他のタイミングでエラーが発生した場合、コントロールは、ストックエラーイベントを発生させる、 [COleControl:: 焼討 error](reference/colecontrol-class.md#fireerror)を呼び出す必要があります。

発生したエラーの種類を示すには、コントロールはまたはにエラーコードを渡す必要があり `ThrowError` `FireError` ます。 エラーコードは、32ビットの値を持つ OLE ステータスコードです。 可能であれば、OLECTL で定義されている標準のコードセットからエラーコードを選択します。H ヘッダーファイル。 次の表は、これらのコードをまとめたものです。

### <a name="activex-control-error-codes"></a>ActiveX コントロールのエラーコード

|エラー|説明|
|-----------|-----------------|
|CTL_E_ILLEGALFUNCTIONCALL|無効な関数呼び出し|
|CTL_E_OVERFLOW|オーバーフロー|
|CTL_E_OUTOFMEMORY|メモリ不足|
|CTL_E_DIVISIONBYZERO|0による除算|
|CTL_E_OUTOFSTRINGSPACE|文字列スペースが不足しています。|
|CTL_E_OUTOFSTACKSPACE|スタック領域が不足しています。|
|CTL_E_BADFILENAMEORNUMBER|ファイル名または番号が正しくありません。|
|CTL_E_FILENOTFOUND|ファイルが見つからない|
|CTL_E_BADFILEMODE|ファイル モードが正しくありません。|
|CTL_E_FILEALREADYOPEN|ファイルは既に開かれています。|
|CTL_E_DEVICEIOERROR|デバイス I/O エラーです。|
|CTL_E_FILEALREADYEXISTS|ファイルは既に存在します|
|CTL_E_BADRECORDLENGTH|レコード長が正しくありません。|
|CTL_E_DISKFULL|ディスクがいっぱいです|
|CTL_E_BADRECORDNUMBER|レコード番号が正しくありません|
|CTL_E_BADFILENAME|ファイル名が正しくありません|
|CTL_E_TOOMANYFILES|ファイルが多すぎます。|
|CTL_E_DEVICEUNAVAILABLE|デバイスが準備されていません|
|CTL_E_PERMISSIONDENIED|アクセス許可は拒否されました|
|CTL_E_DISKNOTREADY|ディスクが準備されていません|
|CTL_E_PATHFILEACCESSERROR|パス/ファイルアクセスエラー|
|CTL_E_PATHNOTFOUND|パスが見つかりません。|
|CTL_E_INVALIDPATTERNSTRING|正しくないパターン文字列|
|CTL_E_INVALIDUSEOFNULL|NULL の使用は無効です|
|CTL_E_INVALIDFILEFORMAT|ファイル形式が無効です|
|CTL_E_INVALIDPROPERTYVALUE|無効なプロパティ値|
|CTL_E_INVALIDPROPERTYARRAYINDEX|無効なプロパティ配列インデックス|
|CTL_E_SETNOTSUPPORTEDATRUNTIME|Set は実行時にはサポートされません|
|CTL_E_SETNOTSUPPORTED|Set はサポートされません。読み取り専用のプロパティです。|
|CTL_E_NEEDPROPERTYARRAYINDEX|プロパティ配列のインデックスが必要です。|
|CTL_E_SETNOTPERMITTED|Set は使用できません|
|CTL_E_GETNOTSUPPORTEDATRUNTIME|Get は実行時にはサポートされません|
|CTL_E_GETNOTSUPPORTED|Get はサポートされません。書き込み専用のプロパティです|
|CTL_E_PROPERTYNOTFOUND|プロパティが見つかりません。|
|CTL_E_INVALIDCLIPBOARDFORMAT|クリップボードの形式が無効です|
|CTL_E_INVALIDPICTURE|無効な画像|
|CTL_E_PRINTERERROR|プリンター エラーです|
|CTL_E_CANTSAVEFILETOTEMP|ファイルを TEMP に保存できません|
|CTL_E_SEARCHTEXTNOTFOUND|検索文字列が見つかりませんでした|
|CTL_E_REPLACEMENTSTOOLONG|置換後の文字列が長すぎます|

必要に応じて、CUSTOM_CTL_SCODE マクロを使用して、標準コードのいずれにも含まれない条件のカスタムエラーコードを定義します。 このマクロのパラメーターは、1000 ~ 32767 の範囲の整数である必要があります。 次に例を示します。

[!code-cpp[NVC_MFC_AxUI#37](codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]

既存の VBX コントロールを置き換える ActiveX コントロールを作成する場合は、エラーコードに互換性があることを確認するために、VBX コントロールが使用するのと同じ数値を使用して ActiveX コントロールのエラーコードを定義します。

## <a name="handling-special-keys-in-the-control"></a><a name="_core_handling_special_keys_in_your_control"></a> コントロールでの特殊なキーの処理

場合によっては、特定のキーストロークの組み合わせを特別な方法で処理することが必要になることがあります。たとえば、複数行テキストボックスコントロールで ENTER キーを押すか、方向キー ID が押されたときに編集コントロールのグループ間を移動すると、新しい行を挿入します。

ActiveX コントロールの基本クラスがの場合は `COleControl` 、 [CWnd::P retranslatemessage](reference/cwnd-class.md#pretranslatemessage) をオーバーライドして、コンテナーがメッセージを処理する前にメッセージを処理することができます。 この手法を使用する場合、のオーバーライドでメッセージを処理する場合は、常に **TRUE** を返し `PreTranslateMessage` ます。

次のコード例は、方向キーに関連するメッセージを処理する方法を示しています。

[!code-cpp[NVC_MFC_AxUI#38](codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]

ActiveX コントロールのキーボードインターフェイスを処理する方法の詳細については、ActiveX SDK のドキュメントを参照してください。

## <a name="accessing-dialog-controls-that-are-invisible-at-run-time"></a><a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a> 実行時に非表示になるダイアログコントロールへのアクセス

ユーザーインターフェイスを持たず、実行時に非表示になるダイアログコントロールを作成できます。 実行時に非表示の ActiveX コントロールをダイアログボックスに追加し、 [CWnd:: GetDlgItem](reference/cwnd-class.md#getdlgitem) を使用してコントロールにアクセスした場合、コントロールは正しく機能しません。 代わりに、次のいずれかの方法を使用して、コントロールを表すオブジェクトを取得する必要があります。

- メンバー変数の追加ウィザードを使用して、[ **制御変数** ] を選択し、コントロールの ID を選択します。 メンバー変数名を入力し、コントロールの **種類** としてコントロールのラッパークラスを選択します。

     または

- ローカル変数とサブクラスをダイアログ項目として宣言します。 次のようなコードを挿入し `CMyCtrl` ます (はラッパークラス、IDC_MYCTRL1 はコントロールの ID です)。

   [!code-cpp[NVC_MFC_AxCont#19](codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](mfc-activex-controls.md)
