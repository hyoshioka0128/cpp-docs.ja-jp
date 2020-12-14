---
description: '詳細: CToolBar クラス'
title: CToolBar クラス
ms.date: 11/04/2016
f1_keywords:
- CToolBar
- AFXEXT/CToolBar
- AFXEXT/CToolBar::CToolBar
- AFXEXT/CToolBar::CommandToIndex
- AFXEXT/CToolBar::Create
- AFXEXT/CToolBar::CreateEx
- AFXEXT/CToolBar::GetButtonInfo
- AFXEXT/CToolBar::GetButtonStyle
- AFXEXT/CToolBar::GetButtonText
- AFXEXT/CToolBar::GetItemID
- AFXEXT/CToolBar::GetItemRect
- AFXEXT/CToolBar::GetToolBarCtrl
- AFXEXT/CToolBar::LoadBitmap
- AFXEXT/CToolBar::LoadToolBar
- AFXEXT/CToolBar::SetBitmap
- AFXEXT/CToolBar::SetButtonInfo
- AFXEXT/CToolBar::SetButtons
- AFXEXT/CToolBar::SetButtonStyle
- AFXEXT/CToolBar::SetButtonText
- AFXEXT/CToolBar::SetHeight
- AFXEXT/CToolBar::SetSizes
helpviewer_keywords:
- CToolBar [MFC], CToolBar
- CToolBar [MFC], CommandToIndex
- CToolBar [MFC], Create
- CToolBar [MFC], CreateEx
- CToolBar [MFC], GetButtonInfo
- CToolBar [MFC], GetButtonStyle
- CToolBar [MFC], GetButtonText
- CToolBar [MFC], GetItemID
- CToolBar [MFC], GetItemRect
- CToolBar [MFC], GetToolBarCtrl
- CToolBar [MFC], LoadBitmap
- CToolBar [MFC], LoadToolBar
- CToolBar [MFC], SetBitmap
- CToolBar [MFC], SetButtonInfo
- CToolBar [MFC], SetButtons
- CToolBar [MFC], SetButtonStyle
- CToolBar [MFC], SetButtonText
- CToolBar [MFC], SetHeight
- CToolBar [MFC], SetSizes
ms.assetid: e868da26-5e07-4607-9651-e2f863ad9059
ms.openlocfilehash: a4b100af3bcd4aac57cee19bbba9aaded3248188
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345044"
---
# <a name="ctoolbar-class"></a>CToolBar クラス

一連のビットマップ ボタンおよびオプションの区切り記号を含むコントロール バーです。

## <a name="syntax"></a>構文

```
class CToolBar : public CControlBar
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CToolBar:: CToolBar](#ctoolbar)|`CToolBar` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CToolBar:: CommandToIndex](#commandtoindex)|指定されたコマンド ID を持つボタンのインデックスを返します。|
|[CToolBar:: Create](#create)|Windows ツールバーを作成し、オブジェクトにアタッチし `CToolBar` ます。|
|[CToolBar:: CreateEx](#createex)|`CToolBar`埋め込みオブジェクトに対して追加のスタイルを使用してオブジェクトを作成し `CToolBarCtrl` ます。|
|[CToolBar:: GetButtonInfo](#getbuttoninfo)|ボタンの ID、スタイル、およびイメージ番号を取得します。|
|[CToolBar:: GetButtonStyle](#getbuttonstyle)|ボタンのスタイルを取得します。|
|[CToolBar:: GetButtonText](#getbuttontext)|ボタンに表示されるテキストを取得します。|
|[CToolBar:: GetItemID](#getitemid)|指定されたインデックス位置にあるボタンまたは区切り記号のコマンド ID を返します。|
|[CToolBar:: GetItemRect](#getitemrect)|指定したインデックス位置にある項目の表示四角形を取得します。|
|[CToolBar:: GetToolBarCtrl](#gettoolbarctrl)|基になるコモンコントロールに直接アクセスできるようにします。|
|[CToolBar:: LoadBitmap](#loadbitmap)|ビットマップボタンイメージを格納しているビットマップを読み込みます。|
|[CToolBar:: LoadToolBar](#loadtoolbar)|リソースエディターを使用して作成されたツールバーリソースを読み込みます。|
|[CToolBar:: SetBitmap](#setbitmap)|ビットマップイメージを設定します。|
|[CToolBar:: SetButtonInfo](#setbuttoninfo)|ボタンの ID、スタイル、およびイメージ番号を設定します。|
|[CToolBar:: SetButtons](#setbuttons)|ビットマップ内のボタンのスタイルとボタンイメージのインデックスを設定します。|
|[CToolBar:: SetButtonStyle](#setbuttonstyle)|ボタンのスタイルを設定します。|
|[CToolBar:: SetButtonText](#setbuttontext)|ボタンに表示されるテキストを設定します。|
|[CToolBar:: SetHeight](#setheight)|ツールバーの高さを設定します。|
|[CToolBar:: SetSizes](#setsizes)|ボタンとそのビットマップのサイズを設定します。|

## <a name="remarks"></a>解説

ボタンは、プッシュボタン、チェックボックスボタン、オプションボタンのように動作します。 `CToolBar` オブジェクトは、通常、 [CFrameWnd](../../mfc/reference/cframewnd-class.md) または [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)クラスから派生したフレームウィンドウオブジェクトの埋め込みメンバーです。

[CToolBar:: GetToolBarCtrl](#gettoolbarctrl)(MFC 4.0 に新しく追加されたメンバー関数) を使用すると、Windows コモンコントロールによるツールバーのカスタマイズと追加機能のサポートを利用できます。 `CToolBar` メンバー関数は、Windows コモンコントロールのほとんどの機能を提供します。ただし、を呼び出すと `GetToolBarCtrl` 、Windows 95/98 のツールバーの特性をさらに多くのツールバーに与えることができます。 を呼び出すと `GetToolBarCtrl` 、オブジェクトへの参照が返され `CToolBarCtrl` ます。 Windows コモンコントロールを使用したツールバーのデザインの詳細については、「 [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) 」を参照してください。 一般的なコントロールの全般的な情報については、「Windows SDK の [コモンコントロール](/windows/win32/Controls/common-controls-intro) 」を参照してください。

Visual C++ には、ツールバーを作成する2つの方法が用意されています。 リソースエディターを使用してツールバーリソースを作成するには、次の手順を実行します。

1. ツールバーリソースを作成します。

1. オブジェクトを構築 `CToolBar` します。

1. [Create](#create) (または[CreateEx](#createex)) 関数を呼び出して、Windows ツールバーを作成し、オブジェクトにアタッチし `CToolBar` ます。

1. [Loadtoolbar](#loadtoolbar)を呼び出して、ツールバーリソースを読み込みます。

それ以外の場合は、次の手順に従います。

1. オブジェクトを構築 `CToolBar` します。

1. [Create](#create) (または[CreateEx](#createex)) 関数を呼び出して、Windows ツールバーを作成し、オブジェクトにアタッチし `CToolBar` ます。

1. [Loadbitmap](#loadbitmap)を呼び出して、ツールバーボタンイメージを含むビットマップを読み込みます。

1. [Setbuttons](#setbuttons)を呼び出してボタンのスタイルを設定し、各ボタンをビットマップ内のイメージに関連付けます。

ツールバーのすべてのボタンイメージは、1つのビットマップから取得されます。このビットマップには、ボタンごとに1つのイメージが含まれている必要があります。 すべてのイメージのサイズは同じである必要があります。既定値は幅16ピクセル、高さ15ピクセルです。 ビットマップでは、イメージが横に並んでいる必要があります。

関数は、 `SetButtons` コントロール id の配列へのポインターと、配列内の要素の数を指定する整数を受け取ります。 関数は、各ボタンの ID を配列の対応する要素の値に設定し、各ボタンにイメージインデックスを割り当てます。これにより、ビットマップ内のボタンのイメージの位置が指定されます。 配列要素の値が ID_SEPARATOR の場合、イメージインデックスは割り当てられません。

ビットマップ内のイメージの順序は、通常、画面上に描画される順序ですが、 [SetButtonInfo](#setbuttoninfo) 関数を使用すると、イメージの順序と描画順序の関係を変更できます。

ツールバーのすべてのボタンは同じサイズです。 既定値は、 *ソフトウェア設計の Windows インターフェイスガイドライン* に従って、24 x 22 ピクセルです。 画像とボタンの大きさの間に追加のスペースを使用して、画像の周りに境界線を作成します。

各ボタンには1つのイメージがあります。 ボタンのさまざまな状態とスタイル (押されている、上、下、無効、無効、停止、不確定) は、その1つのイメージから生成されます。 ビットマップは任意の色にすることができますが、黒と灰色の網掛けで最適な結果を得ることができます。

> [!WARNING]
> `CToolBar` 最大16色のビットマップをサポートします。 ツールバーエディターに画像を読み込むと、必要に応じて自動的に画像が16色のビットマップに変換され、画像が変換された場合は警告メッセージが表示されます。 (外部エディターを使用してイメージを編集して) 16 色以上のイメージを使用すると、アプリケーションが予期せず動作する可能性があります。

既定では、ツールバーボタンは、プッシュボタンを模倣します。 ただし、ツールバーのボタンには、チェックボックスボタンやラジオボタンを模倣することもできます。 チェックボックスボタンには、オン、オフ、不確定の3つの状態があります。 オプションボタンの状態は [オン] と [オフ] の2つだけです。

配列をポイントせずに個々のボタンまたは区分線のスタイルを設定するには、 [Getbuttonstyle](#getbuttonstyle) を呼び出してスタイルを取得し、ではなく [SetButtonStyle](#setbuttonstyle) を呼び出し `SetButtons` ます。 `SetButtonStyle` は、実行時にボタンのスタイルを変更する場合に最も役立ちます。

ボタンに表示されるテキストを割り当てるには、 [Getbuttontext](#getbuttontext) を呼び出して、ボタンに表示されるテキストを取得し、 [SetButtonText](#setbuttontext) を呼び出してテキストを設定します。

チェックボックスボタンを作成するには、そのボタンにスタイル TBBS_CHECKBOX を割り当てるか、 `CCmdUI` `SetCheck` ON_UPDATE_COMMAND_UI ハンドラーでオブジェクトのメンバー関数を使用します。 を呼び出す `SetCheck` と、プッシュボタンがチェックボックスボタンに変わります。 オフの場合 `SetCheck` は0、checked の場合は1、不確定の場合は2を渡します。

オプションボタンを作成するには、ON_UPDATE_COMMAND_UI ハンドラーから [CCmdUI](../../mfc/reference/ccmdui-class.md) オブジェクトの [SetRadio](../../mfc/reference/ccmdui-class.md#setradio) メンバー関数を呼び出します。 Checked の場合 `SetRadio` は0、チェックされない場合は0の引数を渡します。 無線グループの相互排他的な動作を提供するには、グループ内のすべてのボタンに対して ON_UPDATE_COMMAND_UI ハンドラーが必要です。

の使用方法の詳細については `CToolBar` 、「 [MFC ツールバーの実装](../../mfc/mfc-toolbar-implementation.md) 」および「 [テクニカルノート 31: コントロールバー](../../mfc/tn031-control-bars.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CToolBar`

## <a name="requirements"></a>要件

**ヘッダー:** afxext.h

## <a name="ctoolbarcommandtoindex"></a><a name="commandtoindex"></a> CToolBar:: CommandToIndex

このメンバー関数は、コマンド ID が一致する最初のツールバーボタンのインデックスを返します。この位置は0から始まり `nIDFind` ます。

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>パラメーター

*nIDFind*<br/>
ツールバーボタンのコマンド ID。

### <a name="return-value"></a>戻り値

ボタンのインデックス。または、指定されたコマンド ID を持つボタンがない場合は-1。

## <a name="ctoolbarcreate"></a><a name="create"></a> CToolBar:: Create

このメンバー関数は、Windows ツールバー (子ウィンドウ) を作成し、オブジェクトに関連付け `CToolBar` ます。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
ツールバーの親であるウィンドウへのポインター。

*dwStyle*<br/>
ツールバーのスタイル。 サポートされている追加のツールバースタイルは次のとおりです。

- CBRS_TOP コントロールバーは、フレームウィンドウの上部に表示されます。

- CBRS_BOTTOM コントロールバーは、フレームウィンドウの下部に表示されます。

- 親のサイズを変更しても、コントロールバー CBRS_NOALIGN は再配置されません。

- CBRS_TOOLTIPS コントロールバーには、ツールヒントが表示されます。

- CBRS_SIZE_DYNAMIC コントロールバーは動的です。

- CBRS_SIZE_FIXED コントロールバーは固定されています。

- CBRS_FLOATING コントロールバーはフローティングです。

- CBRS_FLYBY ステータスバーには、ボタンに関する情報が表示されます。

- CBRS_HIDE_INPLACE コントロールバーがユーザーに表示されません。

*nID*<br/>
ツールバーの子ウィンドウ ID。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>解説

また、ツールバーの高さを既定値に設定します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]

## <a name="ctoolbarcreateex"></a><a name="createex"></a> CToolBar:: CreateEx

この関数を呼び出して、Windows ツールバー (子ウィンドウ) を作成し、オブジェクトに関連付け `CToolBar` ます。

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = TBSTYLE_FLAT,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_ALIGN_TOP,
    CRect rcBorders = CRect(
    0,
    0,
    0,
    0),
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
ツールバーの親であるウィンドウへのポインター。

*dwCtrlStyle*<br/>
埋め込み [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) オブジェクトを作成するための追加のスタイル。 既定では、この値は TBSTYLE_FLAT に設定されます。 ツールバーのスタイルの完全な一覧については、「 *dwStyle*」を参照してください。

*dwStyle*<br/>
ツールバーのスタイル。 適切なスタイルの一覧については、「Windows SDK の [ツールバーコントロールとボタンスタイル](/windows/win32/Controls/toolbar-control-and-button-styles) 」を参照してください。

*rcBorders*<br/>
ツールバーウィンドウの境界線の幅を定義する、 [CRect](../../atl-mfc-shared/reference/crect-class.md) オブジェクト。 既定では、これらの罫線は0、0、0、0に設定されます。その結果、境界線のないツールバーウィンドウになります。

*nID*<br/>
ツールバーの子ウィンドウ ID。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>解説

また、ツールバーの高さを既定値に設定します。

`CreateEx`埋め込みのツールバーコントロールの作成中に特定のスタイルが存在する必要がある場合は、 [Create](#create)ではなくを使用します。 たとえば、Internet Explorer 4 のツールバーに似たツールバーを作成するには、[ *dwCtrlStyle* ] を TBSTYLE_FLAT &#124; TBSTYLE_TRANSPARENT に設定します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]

## <a name="ctoolbarctoolbar"></a><a name="ctoolbar"></a> CToolBar:: CToolBar

このメンバー関数は、 `CToolBar` オブジェクトを構築し、既定のサイズを設定します。

```
CToolBar();
```

### <a name="remarks"></a>解説

[Create](#create) member 関数を呼び出して、ツールバーウィンドウを作成します。

## <a name="ctoolbargetbuttoninfo"></a><a name="getbuttoninfo"></a> CToolBar:: GetButtonInfo

このメンバー関数は、NIndex によって指定された場所にあるツールバーボタンまたは区切り記号のコントロール ID、スタイル、およびイメージインデックスを取得し *ます。*

```cpp
void GetButtonInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& iImage) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
情報を取得するツールバーボタンまたは区切り記号のインデックス。

*nID*<br/>
ボタンのコマンド ID に設定されている UINT への参照。

*nStyle*<br/>
ボタンのスタイルに設定されている UINT への参照。

*iImage*<br/>
ビットマップ内のボタンのイメージのインデックスに設定されている整数への参照。

### <a name="remarks"></a>解説

これらの値は、 *nID*、 *nstyle*、および *iImage* によって参照される変数に割り当てられます。 イメージインデックスは、すべてのツールバーボタンの画像を含むビットマップ内の画像の位置です。 最初のイメージは0の位置にあります。

*NIndex* で区切り記号を指定した場合、 *iImage* はピクセル単位で区切り記号の幅に設定されます。

## <a name="ctoolbargetbuttonstyle"></a><a name="getbuttonstyle"></a> CToolBar:: GetButtonStyle

このメンバー関数を呼び出して、ツールバーのボタンまたは区切り記号のスタイルを取得します。

```
UINT GetButtonStyle(int nIndex) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
取得するツールバーボタンまたは区分線スタイルのインデックス。

### <a name="return-value"></a>戻り値

*NIndex* によって指定されたボタンまたは区切り記号のスタイル。

### <a name="remarks"></a>解説

ボタンのスタイルによって、ボタンの表示方法と、ユーザー入力に対する応答方法が決まります。 ボタンスタイルの例については、「 [SetButtonStyle](#setbuttonstyle) 」を参照してください。

## <a name="ctoolbargetbuttontext"></a><a name="getbuttontext"></a> CToolBar:: GetButtonText

ボタンに表示されるテキストを取得するには、このメンバー関数を呼び出します。

```
CString GetButtonText(int nIndex) const;

void GetButtonText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
取得するテキストのインデックス。

*rString*<br/>
取得するテキストを格納する [CString](../../atl-mfc-shared/reference/cstringt-class.md) オブジェクトへの参照。

### <a name="return-value"></a>戻り値

`CString`ボタンテキストを格納しているオブジェクト。

### <a name="remarks"></a>解説

このメンバー関数の2番目の形式は、 `CString` 文字列テキストをオブジェクトに入力します。

## <a name="ctoolbargetitemid"></a><a name="getitemid"></a> CToolBar:: GetItemID

このメンバー関数は、 *nIndex* によって指定されたボタンまたは区切り記号のコマンド ID を返します。

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
ID を取得する項目のインデックス。

### <a name="return-value"></a>戻り値

*NIndex* によって指定されたボタンまたは区切り記号のコマンド ID。

### <a name="remarks"></a>解説

区切り記号は ID_SEPARATOR を返します。

## <a name="ctoolbargetitemrect"></a><a name="getitemrect"></a> CToolBar:: GetItemRect

このメンバー関数は、 `RECT` *lpRect* に含まれるアドレスが、 *nIndex* によって指定されたボタンまたは区切り記号の座標を持つ構造体を塗りつぶします。

```
virtual void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
四角形の座標を取得する項目 (ボタンまたは区切り記号) のインデックス。

*lpRect*<br/>
項目の座標を格納する [RECT](/windows/win32/api/windef/ns-windef-rect) 構造体のアドレス。

### <a name="remarks"></a>解説

座標は、ツールバーの左上隅を基準とした相対的なピクセル数です。

`GetItemRect`コンボボックスまたは他のコントロールで置き換える区切り記号の座標を取得するには、を使用します。

### <a name="example"></a>例

  「 [CToolBar:: SetSizes](#setsizes)」の例を参照してください。

## <a name="ctoolbargettoolbarctrl"></a><a name="gettoolbarctrl"></a> CToolBar:: GetToolBarCtrl

このメンバー関数は、基になるコモンコントロールに直接アクセスできるようにします。

```
CToolBarCtrl& GetToolBarCtrl() const;
```

### <a name="return-value"></a>戻り値

`CToolBarCtrl` オブジェクトへの参照です。

### <a name="remarks"></a>解説

`GetToolBarCtrl`を使用すると、Windows ツールバーコモンコントロールの機能を活用し、ツールバーのカスタマイズに[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)が提供するサポートを利用できます。

コモンコントロールの使用方法の詳細については、Windows SDK の「 [コントロール](../../mfc/controls-mfc.md) と [コモンコントロール](/windows/win32/Controls/common-controls-intro) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]

## <a name="ctoolbarloadbitmap"></a><a name="loadbitmap"></a> CToolBar:: LoadBitmap

またはで指定されたビットマップを読み込むには、このメンバー関数を呼び出し `lpszResourceName` `nIDResource` ます。

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>パラメーター

*lpszResourceName*<br/>
読み込むビットマップのリソース名へのポインター。

*nIDResource*<br/>
読み込むビットマップのリソース ID。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>解説

ビットマップには、ツールバーボタンごとに1つのイメージが含まれている必要があります。 画像のサイズが標準サイズ (幅16ピクセル、高さ15ピクセル) でない場合は、 [setsizes](#setsizes) を呼び出して、ボタンのサイズと画像を設定します。

> [!WARNING]
> `CToolBar` 最大16色のビットマップをサポートします。 ツールバーエディターに画像を読み込むと、必要に応じて自動的に画像が16色のビットマップに変換され、画像が変換された場合は警告メッセージが表示されます。 (外部エディターを使用してイメージを編集して) 16 色以上のイメージを使用すると、アプリケーションが予期せず動作する可能性があります。

## <a name="ctoolbarloadtoolbar"></a><a name="loadtoolbar"></a> CToolBar:: LoadToolBar

このメンバー関数を呼び出して、 *lpszresourcename* *nIDResource* によって指定されたツールバーを読み込みます。

```
BOOL LoadToolBar(LPCTSTR lpszResourceName);
BOOL LoadToolBar(UINT nIDResource);
```

### <a name="parameters"></a>パラメーター

*lpszResourceName*<br/>
読み込むツールバーのリソース名へのポインター。

*nIDResource*<br/>
読み込むツールバーのリソース ID。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>解説

ツールバーリソースの作成の詳細については、「」の [ツールバーエディター](../../windows/toolbar-editor.md) を参照してください。

### <a name="example"></a>例

  「 [CToolBar:: CreateEx](#createex)」の例を参照してください。

## <a name="ctoolbarsetbitmap"></a><a name="setbitmap"></a> CToolBar:: SetBitmap

ツールバーのビットマップイメージを設定するには、このメンバー関数を呼び出します。

```
BOOL SetBitmap(HBITMAP hbmImageWell);
```

### <a name="parameters"></a>パラメーター

*hbmImageWell*<br/>
ツールバーに関連付けられているビットマップイメージのハンドル。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>解説

たとえば、 `SetBitmap` ユーザーがボタンのアクションを変更するドキュメントに対して操作を実行した後に、を呼び出してビットマップイメージを変更します。

## <a name="ctoolbarsetbuttoninfo"></a><a name="setbuttoninfo"></a> CToolBar:: SetButtonInfo

このメンバー関数を呼び出して、ボタンのコマンド ID、スタイル、およびイメージ番号を設定します。

```cpp
void SetButtonInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int iImage);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
情報を設定するボタンまたは区切り記号の0から始まるインデックス。

*nID*<br/>
ボタンのコマンド ID が設定される値。

*nStyle*<br/>
新しいボタンスタイル。 次のボタンスタイルがサポートされています。

- TBBS_BUTTON 標準のプッシュボタン (既定)

- TBBS_SEPARATOR 区切り記号

- [自動チェックボックスの TBBS_CHECKBOX] ボタン

- TBBS_GROUP は、ボタンのグループの先頭にマークを付けます

- チェックボックスボタンのグループの開始をマーク TBBS_CHECKGROUP

- TBBS_DROPDOWN ドロップダウンリストボタンを作成します。

- TBBS_AUTOSIZE ボタンの幅は、イメージのサイズではなく、ボタンのテキストに基づいて計算されます。

- TBBS_NOPREFIX ボタンテキストには、アクセラレータプレフィックスが関連付けられていません。

*iImage*<br/>
ビットマップ内のボタンのイメージの新しいインデックス。

### <a name="remarks"></a>解説

TBBS_SEPARATOR スタイルを持つ区切り記号の場合、この関数は、区切り記号の幅をピクセル単位で *iImage* に格納されている値に設定します。

> [!NOTE]
> また、 *Nstyle* パラメーターを使用してボタンの状態を設定することもできます。ただし、ボタンの状態は [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) ハンドラーによって制御されるため、を使用して設定した状態は、 `SetButtonInfo` 次のアイドル処理時に失われます。 詳細については、「 [How To Update User-Interface Objects](../../mfc/how-to-update-user-interface-objects.md) and [テクニカルノート 31: Control bar](../../mfc/tn031-control-bars.md) 」を参照してください。

ビットマップイメージとボタンの詳細については、「 [ctoolbar](../../mfc/reference/ctoolbar-class.md) の概要」と「 [Ctoolbar:: loadbitmap](#loadbitmap)」を参照してください。

## <a name="ctoolbarsetbuttons"></a><a name="setbuttons"></a> CToolBar:: SetButtons

このメンバー関数は、各ツールバーボタンのコマンド ID を、配列の *Lpidarray* の対応する要素によって指定された値に設定します。

```
BOOL SetButtons(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>パラメーター

*lpIDArray*<br/>
コマンド Id の配列へのポインター。 空のボタンを割り当てるには NULL を指定できます。

*nIDCount*<br/>
*Lpidarray* が指す配列内の要素の数。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>解説

配列の要素に ID_SEPARATOR 値がある場合、ツールバーの対応する位置に区切り記号が作成されます。 また、この関数は、各ボタンのスタイルを TBBS_BUTTON に設定し、各区切り記号のスタイルを TBBS_SEPARATOR に設定し、イメージのインデックスを各ボタンに割り当てます。 イメージインデックスは、ビットマップ内のボタンのイメージの位置を指定します。

この関数では区切り記号にイメージインデックスが割り当てられないため、ビットマップの区切り記号を考慮する必要はありません。 ツールバーの位置が0、1、3で、区切り記号が2の場合、ビットマップ内の位置が0、1、および2の画像はそれぞれ、0、1、3の位置にあるボタンに割り当てられます。

*Lpidarray* が NULL の場合、この関数は、 *nIDCount* によって指定された項目の数に領域を割り当てます。 各項目の属性を設定するには、 [SetButtonInfo](#setbuttoninfo) を使用します。

## <a name="ctoolbarsetbuttonstyle"></a><a name="setbuttonstyle"></a> CToolBar:: SetButtonStyle

このメンバー関数を呼び出して、ボタンまたは区切り記号のスタイル、またはグループボタンを設定します。

```cpp
void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
情報を設定するボタンまたは区切り記号のインデックス。

*nStyle*<br/>
ボタンのスタイル。 次のボタンスタイルがサポートされています。

- TBBS_BUTTON 標準のプッシュボタン (既定)

- TBBS_SEPARATOR 区切り記号

- [自動チェックボックスの TBBS_CHECKBOX] ボタン

- TBBS_GROUP は、ボタンのグループの先頭にマークを付けます

- チェックボックスボタンのグループの開始をマーク TBBS_CHECKGROUP

- TBBS_DROPDOWN ドロップダウンリストボタンを作成するには

- TBBS_AUTOSIZE ボタンの幅は、イメージのサイズではなく、ボタンのテキストに基づいて計算されます。

- ボタンのテキストにアクセラレータプレフィックスが関連付けられていない TBBS_NOPREFIX

### <a name="remarks"></a>解説

ボタンのスタイルによって、ボタンの表示方法と、ユーザー入力に対する応答方法が決まります。

を呼び出す前に `SetButtonStyle` 、 [getbuttonstyle](#getbuttonstyle) メンバー関数を呼び出して、ボタンまたは区切り記号のスタイルを取得します。

> [!NOTE]
> また、 *Nstyle* パラメーターを使用してボタンの状態を設定することもできます。ただし、ボタンの状態は [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) ハンドラーによって制御されるため、を使用して設定した状態は、 `SetButtonStyle` 次のアイドル処理時に失われます。 詳細については、「 [How To Update User-Interface Objects](../../mfc/how-to-update-user-interface-objects.md) and [テクニカルノート 31: Control bar](../../mfc/tn031-control-bars.md) 」を参照してください。

## <a name="ctoolbarsetbuttontext"></a><a name="setbuttontext"></a> CToolBar:: SetButtonText

ボタンのテキストを設定するには、この関数を呼び出します。

```
BOOL SetButtonText(
    int nIndex,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
テキストを設定するボタンのインデックス。

*lpszText*<br/>
ボタンに設定するテキストを指します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="example"></a>例

  「 [CToolBar:: GetToolBarCtrl](#gettoolbarctrl)」の例を参照してください。

## <a name="ctoolbarsetheight"></a><a name="setheight"></a> CToolBar:: SetHeight

このメンバー関数は、ツールバーの高さを、 *cyheight* で指定されたピクセル単位の値に設定します。

```cpp
void SetHeight(int cyHeight);
```

### <a name="parameters"></a>パラメーター

*cyHeight*<br/>
ツールバーの高さ (ピクセル単位)。

### <a name="remarks"></a>解説

[Setsizes](#setsizes)を呼び出した後、このメンバー関数を使用して、標準のツールバーの高さをオーバーライドします。 高さが小さすぎる場合、ボタンは下部にクリップされます。

この関数が呼び出されていない場合、フレームワークはボタンのサイズを使用して、ツールバーの高さを決定します。

## <a name="ctoolbarsetsizes"></a><a name="setsizes"></a> CToolBar:: SetSizes

このメンバー関数を呼び出して、ツールバーのボタンをサイズ (ピクセル *単位) に* 設定します。

```cpp
void SetSizes(
    SIZE sizeButton,
    SIZE sizeImage);
```

### <a name="parameters"></a>パラメーター

*sizeButton*<br/>
各ボタンのサイズ (ピクセル単位)。

*sizeImage*<br/>
各イメージのサイズ (ピクセル単位)。

### <a name="remarks"></a>解説

*Sizeimage* パラメーターには、ツールバーのビットマップ内のイメージのサイズ (ピクセル単位) が含まれている必要があります。 *Sizebutton* の大きさは、イメージを保持するのに十分であり、幅と高さが6ピクセルである必要があります。 また、この関数は、ボタンに応じてツールバーの高さを設定します。

このメンバー関数は、ボタンおよびイメージサイズのソフトウェア設計の推奨事項 *について、Windows インターフェイスのガイドライン* に従っていないツールバーに対してのみ呼び出します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]

## <a name="see-also"></a>関連項目

[MFC のサンプル CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[MFC のサンプル DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[MFC のサンプル DOCKTOOL](../../overview/visual-cpp-samples.md)<br/>
[CControlBar クラス](../../mfc/reference/ccontrolbar-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl クラス](../../mfc/reference/ctoolbarctrl-class.md)<br/>
[CControlBar クラス](../../mfc/reference/ccontrolbar-class.md)
