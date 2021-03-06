---
title: 'WM_ で始まるメッセージのハンドラー : A - C'
ms.date: 11/04/2016
f1_keywords:
- ON_WM_CREATE
- ON_WM_COMPACTING
- ON_WM_CHARTOITEM
- ON_WM_ASKCBFORMATNAME
- ON_WM_CTLCOLOR
- ON_WM_COMPAREITEM
- ON_WM_CHILDACTIVATE
- ON_WM_CONTEXTMENU
- ON_WM_ACTIVATE
- ON_WM_CANCELMODE
- ON_WM_CLOSE
- ON_WM_CAPTURECHANGED
- ON_WM_ACTIVATEAPP
- ON_WM_CHAR
- ON_WM_CHANGECBCHAIN
helpviewer_keywords:
- ON_WM_COMPACTING [MFC]
- ON_WM_COMPAREITEM [MFC]
- ON_WM_CLOSE [MFC]
- ON_WM_CTLCOLOR [MFC]
- ON_WM_CHAR [MFC]
- ON_WM_CAPTURECHANGED [MFC]
- ON_WM_CHARTOITEM [MFC]
- ON_WM_CREATE [MFC]
- ON_WM_ACTIVATE [MFC]
- ON_WM_CONTEXTMENU [MFC]
- ON_WM_CANCELMODE [MFC]
- ON_WM_ASKCBFORMATNAME [MFC]
- ON_WM_CHILDACTIVATE [MFC]
- WM_ messages [MFC]
- ON_WM_ACTIVATEAPP [MFC]
- ON_WM_CHANGECBCHAIN
ms.assetid: 4e315896-d646-4b87-b0ab-41a4a753b045
ms.openlocfilehash: 67ab1620d0ad815cc070935a2b314bbfa2ef1408
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596834"
---
# <a name="wm-message-handlers-a---c"></a>WM_ で始まるメッセージのハンドラー : A - C

左側で、次のマップ エントリは、右側の関数プロトタイプに対応します。

|マップ エントリ|関数プロトタイプ|
|---------------|------------------------|
|ON_WM_ACTIVATE()|afx_msg void [OnActivate](../../mfc/reference/cwnd-class.md#onactivate)(UINT、CWnd\*BOOL);|
|ON_WM_ACTIVATEAPP()|afx_msg void [OnActivateApp](../../mfc/reference/cwnd-class.md#onactivateapp)(BOOL、DWORD) です。|
|ON_WM_APPCOMMAND()|afx_msg void [OnAppCommand](../../mfc/reference/cwnd-class.md#onappcommand)(CWnd\*UINT, UINT, UINT)。|
|ON_WM_ASKCBFORMATNAME()|afx_msg void [OnAskCbFormatName](../../mfc/reference/cwnd-class.md#onaskcbformatname)(UINT, LPSTR)。|
|ON_WM_CANCELMODE()|afx_msg void [OnCancelMode](../../mfc/reference/cwnd-class.md#oncancelmode)();|
|ON_WM_CAPTURECHANGED()|afx_msg void [OnCaptureChanged](../../mfc/reference/cwnd-class.md#oncapturechanged)(CWnd\*)。|
|ON_WM_CHANGECBCHAIN()|afx_msg void [OnChangeCbChain](../../mfc/reference/cwnd-class.md#onchangecbchain)(HWND, HWND)。|
|ON_WM_CHAR()|afx_msg void [OnChar](../../mfc/reference/cwnd-class.md#onchar)(UINT, UINT, UINT)|
|ON_WM_CHARTOITEM()|afx_msg int [OnCharToItem](../../mfc/reference/cwnd-class.md#onchartoitem)(UINT、CWnd\*UINT)。|
|ON_WM_CHILDACTIVATE()|afx_msg void [OnChildActivate](../../mfc/reference/cwnd-class.md#onchildactivate)();|
|ON_WM_CLIPBOARDUPDATE()|afx_msg void [OnClipboardUpdate](../../mfc/reference/cwnd-class.md#onclipboardupdate)();|
|ON_WM_CLOSE()|afx_msg void [OnClose](../../mfc/reference/cwnd-class.md#onclose)();|
|ON_WM_COMPACTING()|afx_msg void [OnCompacting](../../mfc/reference/cwnd-class.md#oncompacting)(UINT)。|
|ON_WM_COMPAREITEM()|afx_msg int [OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)(LPCOMPAREITEMSTRUCT)。|
|ON_WM_CONTEXTMENU()|afx_msg void [OnContextMenu](../../mfc/reference/cwnd-class.md#oncontextmenu)(CWnd\*CPoint)。|
|ON_WM_COPYDATA()|afx_msg BOOL [OnCopyData](../../mfc/reference/cwnd-class.md#oncopydata)(CWnd\*我が物、COPYDATASTRUCT\* pCopyDataStruct)。|
|ON_WM_CREATE()|afx_msg int [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)(LPCREATESTRUCT)。|
|ON_WM_CTLCOLOR()|HBRUSH afx_msg [OnCtlColor](../../mfc/reference/cwnd-class.md#onctlcolor)(CDC\*、CWnd\*UINT)。|

## <a name="see-also"></a>関連項目

[メッセージ マップ](../../mfc/reference/message-maps-mfc.md)<br/>
[WM_ で始まるメッセージのハンドラー](../../mfc/reference/handlers-for-wm-messages.md)

