---
description: '詳細情報: CVSListBox クラス'
title: CVSListBox クラス
ms.date: 11/19/2018
f1_keywords:
- CVSListBox
- AFXVSLISTBOX/CVSListBox
- AFXVSLISTBOX/CVSListBox::CVSListBox
- AFXVSLISTBOX/CVSListBox::AddItem
- AFXVSLISTBOX/CVSListBox::EditItem
- AFXVSLISTBOX/CVSListBox::GetCount
- AFXVSLISTBOX/CVSListBox::GetItemData
- AFXVSLISTBOX/CVSListBox::GetItemText
- AFXVSLISTBOX/CVSListBox::GetSelItem
- AFXVSLISTBOX/CVSListBox::RemoveItem
- AFXVSLISTBOX/CVSListBox::SelectItem
- AFXVSLISTBOX/CVSListBox::SetItemData
- AFXVSLISTBOX/CVSListBox::GetListHwnd
helpviewer_keywords:
- CVSListBox [MFC], CVSListBox
- CVSListBox [MFC], AddItem
- CVSListBox [MFC], EditItem
- CVSListBox [MFC], GetCount
- CVSListBox [MFC], GetItemData
- CVSListBox [MFC], GetItemText
- CVSListBox [MFC], GetSelItem
- CVSListBox [MFC], RemoveItem
- CVSListBox [MFC], SelectItem
- CVSListBox [MFC], SetItemData
- CVSListBox [MFC], GetListHwnd
ms.assetid: c79be7b4-46ed-4af8-a41e-68962782d8ef
ms.openlocfilehash: 6912eccd4cc8e7c78407d0cda0a0dc1305d0bde8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344979"
---
# <a name="cvslistbox-class"></a>CVSListBox クラス

クラスは、 `CVSListBox` 編集可能なリストコントロールをサポートしています。

## <a name="syntax"></a>構文

```
class CVSListBox : public CVSListBoxBase
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CVSListBox:: CVSListBox](#cvslistbox)|`CVSListBox` オブジェクトを構築します。|
|`CVSListBox::~CVSListBox`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CVSListBox:: AddItem](#additem)|リストコントロールに文字列を追加します。 ( `CVSListBoxBase::AddItem`をオーバーライドします)。|
|[CVSListBox:: EditItem](#edititem)|リストコントロール項目のテキストに対して編集操作を開始します。 ( `CVSListBoxBase::EditItem`をオーバーライドします)。|
|[CVSListBox:: GetCount](#getcount)|編集可能なリストコントロール内の文字列の数を取得します。 ( `CVSListBoxBase::GetCount`をオーバーライドします)。|
|[CVSListBox:: GetItemData](#getitemdata)|編集可能なリストコントロール項目に関連付けられている、アプリケーション固有の32ビット値を取得します。 ( `CVSListBoxBase::GetItemData`をオーバーライドします)。|
|[CVSListBox:: GetItemText](#getitemtext)|編集可能なリストコントロール項目のテキストを取得します。 ( `CVSListBoxBase::GetItemText`をオーバーライドします)。|
|[CVSListBox:: GetSelItem](#getselitem)|編集可能なリストコントロール内で現在選択されている項目の0から始まるインデックスを取得します。 ( `CVSListBoxBase::GetSelItem`をオーバーライドします)。|
|`CVSListBox::PreTranslateMessage`|[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)および[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)の Windows 関数にディスパッチされる前に、ウィンドウメッセージを変換します。 詳細およびメソッドの構文については、「 [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)」を参照してください。 ( `CVSListBoxBase::PreTranslateMessage`をオーバーライドします)。|
|[CVSListBox:: RemoveItem](#removeitem)|編集可能なリストコントロールから項目を削除します。 ( `CVSListBoxBase::RemoveItem`をオーバーライドします)。|
|[CVSListBox:: SelectItem](#selectitem)|編集可能なリストコントロール文字列を選択します。 ( `CVSListBoxBase::SelectItem`をオーバーライドします)。|
|[CVSListBox:: SetItemData](#setitemdata)|アプリケーション固有の32ビット値を、編集可能なリストコントロール項目に関連付けます。 ( `CVSListBoxBase::SetItemData`をオーバーライドします)。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CVSListBox:: GetListHwnd](#getlisthwnd)|現在の埋め込みリストビューコントロールへのハンドルを返します。|

## <a name="remarks"></a>解説

クラスには、 `CVSListBox` ユーザーがリストコントロール内の項目を作成、変更、削除、または再配置できるようにする一連の編集ボタンが用意されています。

次に、編集可能なリストコントロールの画像を示します。 2番目のリストエントリ ("Item2" というタイトル) が編集用に選択されています。

![CVSListBox コントロール](../../mfc/reference/media/cvslistbox.png "CVSListBox コントロール")

リソースエディターを使用して編集可能なリストコントロールを追加する場合、エディターの [ **ツールボックス** ] ウィンドウには、事前に定義された編集可能なリストコントロールが用意されていないことに注意してください。 代わりに、 **グループボックス** コントロールなどの静的コントロールを追加します。 フレームワークでは、静的コントロールをプレースホルダーとして使用して、編集可能なリストコントロールのサイズと位置を指定します。

ダイアログボックステンプレートで編集可能なリストコントロールを使用するには、 `CVSListBox` ダイアログボックスクラスで変数を宣言します。 変数とコントロールの間のデータ交換をサポートするには、 `DDX_Control` `DoDataExchange` ダイアログボックスのメソッドでマクロエントリを定義します。 既定では、編集可能なリストコントロールは編集ボタンなしで作成されます。 継承された CVSListBoxBase:: SetStandardButtons メソッドを使用して、[編集] ボタンを有効にします。

詳細については、サンプルディレクトリ、 `New Controls` サンプル、Page3 ファイルと Page3 ファイルを参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CStatic](../../mfc/reference/cstatic-class.md)

`CVSListBoxBase`

[CVSListBox](../../mfc/reference/cvslistbox-class.md)

## <a name="requirements"></a>要件

**ヘッダー:** afxvslistbox

## <a name="cvslistboxadditem"></a><a name="additem"></a> CVSListBox:: AddItem

リストコントロールに文字列を追加します。

```
virtual int AddItem(
    const CString& strIext,
    DWORD_PTR dwData=0,
    int iIndex=-1);
```

### <a name="parameters"></a>パラメーター

*ストライプ Ext*<br/>
から文字列への参照。

*dwData*<br/>
から文字列に関連付けられているアプリケーション固有の32ビット値。 既定値は 0 です。

*iIndex*<br/>
から文字列を保持する位置の、0から始まるインデックス番号。 *IIndex* パラメーターが-1 の場合、文字列はリストの末尾に追加されます。 既定値は -1 です。

### <a name="return-value"></a>戻り値

リストコントロール内の文字列の位置の0から始まるインデックス。

### <a name="remarks"></a>解説

*Dwdata* パラメーターによって指定された値を取得するには、 [CVSListBox:: GetItemData](#getitemdata)メソッドを使用します。 この値には、アプリケーション固有の整数または他のデータへのポインターを指定できます。

## <a name="cvslistboxcvslistbox"></a><a name="cvslistbox"></a> CVSListBox:: CVSListBox

`CVSListBox` オブジェクトを構築します。

```
CVSListBox();
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>解説

## <a name="cvslistboxedititem"></a><a name="edititem"></a> CVSListBox:: EditItem

リストコントロール項目のテキストに対して編集操作を開始します。

```
virtual BOOL EditItem(int iIndex);
```

### <a name="parameters"></a>パラメーター

*iIndex*<br/>
からリストコントロール項目の0から始まるインデックス。

### <a name="return-value"></a>戻り値

編集操作が正常に開始された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>解説

ユーザーは、項目のラベルをダブルクリックするか、項目にフォーカスがあるときに **F2** キーまたは **space** キーを押すことによって、編集操作を開始します。

## <a name="cvslistboxgetcount"></a><a name="getcount"></a> CVSListBox:: GetCount

編集可能なリストコントロール内の文字列の数を取得します。

```
virtual int GetCount() const;
```

### <a name="return-value"></a>戻り値

リスト コントロールの項目の数。

### <a name="remarks"></a>解説

カウントは、インデックスが0から始まるため、最後の項目のインデックス値よりも1大きいことに注意してください。

## <a name="cvslistboxgetitemdata"></a><a name="getitemdata"></a> CVSListBox:: GetItemData

編集可能なリストコントロール項目に関連付けられている、アプリケーション固有の32ビット値を取得します。

```
virtual DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>パラメーター

*iIndex*<br/>
から編集可能なリストコントロール項目の0から始まるインデックス。

### <a name="return-value"></a>戻り値

指定した項目に関連付けられている32ビット値。

### <a name="remarks"></a>解説

[CVSListBox:: SetItemData](#setitemdata)または[CVSListBox:: AddItem](#additem)メソッドを使用して、32ビットの値をリストコントロール項目に関連付けます。 この値には、アプリケーション固有の整数または他のデータへのポインターを指定できます。

## <a name="cvslistboxgetitemtext"></a><a name="getitemtext"></a> CVSListBox:: GetItemText

編集可能なリストコントロール項目のテキストを取得します。

```
virtual CString GetItemText(int iIndex) const;
```

### <a name="parameters"></a>パラメーター

*iIndex*<br/>
から編集可能なリストコントロール項目の0から始まるインデックス。

### <a name="return-value"></a>戻り値

指定した項目のテキストを格納している [CString](../../atl-mfc-shared/reference/cstringt-class.md) オブジェクト。

### <a name="remarks"></a>解説

## <a name="cvslistboxgetlisthwnd"></a><a name="getlisthwnd"></a> CVSListBox:: GetListHwnd

現在の埋め込みリストビューコントロールへのハンドルを返します。

```
virtual HWND GetListHwnd() const;
```

### <a name="return-value"></a>戻り値

埋め込まれたリストビューコントロールへのハンドル。

### <a name="remarks"></a>解説

このメソッドを使用して、クラスをサポートする埋め込みリストビューコントロールへのハンドルを取得し `CVSListBox` ます。

## <a name="cvslistboxgetselitem"></a><a name="getselitem"></a> CVSListBox:: GetSelItem

編集可能なリストコントロール内で現在選択されている項目の0から始まるインデックスを取得します。

```
virtual int GetSelItem() const;
```

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は、現在選択されている項目の0から始まるインデックス。それ以外の場合は-1。

### <a name="remarks"></a>解説

## <a name="cvslistboxremoveitem"></a><a name="removeitem"></a> CVSListBox:: RemoveItem

編集可能なリストコントロールから項目を削除します。

```
virtual BOOL RemoveItem(int iIndex);
```

### <a name="parameters"></a>パラメーター

*iIndex*<br/>
から編集可能なリストコントロール項目の0から始まるインデックス。

### <a name="return-value"></a>戻り値

指定した項目が削除された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>解説

## <a name="cvslistboxselectitem"></a><a name="selectitem"></a> CVSListBox:: SelectItem

編集可能なリストコントロール文字列を選択します。

```
virtual BOOL SelectItem(int iItem);
```

### <a name="parameters"></a>パラメーター

*iItem*<br/>
から編集可能なリストコントロール項目の0から始まるインデックス。

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>解説

このメソッドは、指定された項目を選択します。必要に応じて、項目をスクロールして表示します。

## <a name="cvslistboxsetitemdata"></a><a name="setitemdata"></a> CVSListBox:: SetItemData

アプリケーション固有の32ビット値を、編集可能なリストコントロール項目に関連付けます。

```
virtual void SetItemData(
    int iIndex,
    DWORD_PTR dwData);
```

### <a name="parameters"></a>パラメーター

*iIndex*<br/>
から編集可能なリストコントロール項目の0から始まるインデックス。

*dwData*<br/>
から32ビット値。 この値には、アプリケーション固有の整数または他のデータへのポインターを指定できます。

### <a name="remarks"></a>解説

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
