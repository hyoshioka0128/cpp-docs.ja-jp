---
title: アプリケーション ウィザードで作成されるフレーム ウィンドウ クラス
ms.date: 11/04/2016
f1_keywords:
- CMainFrame
helpviewer_keywords:
- application wizards [MFC], frame window classes created by
- window classes [MFC]
- classes [MFC], frame-window
- CMDIFrameWnd class [MFC], frame windows
- window classes [MFC], frame
- CFrameWnd class [MFC], frame windows
- CMDIChildWnd class [MFC], frame windows
- frame window classes [MFC], created by application wizards
- CMainFrame class [MFC]
ms.assetid: 9947df73-4470-49a0-ac61-7b6ee401a74e
ms.openlocfilehash: 581ceb25e675da6506d06bca3798fb22ca8fd389
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629256"
---
# <a name="frame-window-classes-created-by-the-application-wizard"></a>アプリケーション ウィザードで作成されるフレーム ウィンドウ クラス

使用すると、[アプリケーション ウィザード](../ide/creating-desktop-projects-by-using-application-wizards.md)アプリケーション ウィザードをアプリケーション、ドキュメント、およびビューのクラスだけでなく、スケルトン アプリケーションを作成するには、アプリケーションのメイン フレーム ウィンドウのフレーム ウィンドウの派生クラスを作成します。 クラスと呼びます`CMainFrame`で既定値、およびそれが含まれるファイルは名前します。H とします。CPP します。

アプリケーションが SDI の場合、`CMainFrame`クラスから派生したクラスは[CFrameWnd](../mfc/reference/cframewnd-class.md)します。

場合は、アプリケーションは、MDI、`CMainFrame`クラスから派生[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)します。 ここで`CMainFrame`メニューのツールバー、およびステータス バーを保持するメインのフレームを実装します。 アプリケーション ウィザードは、の新しいドキュメント フレーム ウィンドウ クラスを派生していません。 既定の実装を使用する代わりに、 [CMDIChildWnd クラス](../mfc/reference/cmdichildwnd-class.md)します。 MFC フレームワークは、それぞれのビューを格納する子ウィンドウを作成します (型のこともある`CScrollView`、 `CEditView`、 `CTreeView`、`CListView`など)、アプリケーションに必要な。 ドキュメント フレーム ウィンドウをカスタマイズする必要がある場合は、新しいドキュメント フレーム ウィンドウ クラスを作成することができます (を参照してください[クラスの追加](../ide/adding-a-class-visual-cpp.md))。

クラスも型のメンバー変数には、ツールバーをサポートする場合は、 [CToolBar](../mfc/reference/ctoolbar-class.md)と[CStatusBar](../mfc/reference/cstatusbar-class.md)と`OnCreate`メッセージ ハンドラー関数を 2 つの初期化[コントロール バー](../mfc/control-bars.md)します。

作成されると、これらのフレーム ウィンドウ クラスが機能しますが、機能強化のため、メンバー変数とメンバー関数を追加する必要があります。 ウィンドウ クラスの他の Windows メッセージを処理することもできます。 詳細については、次を参照してください。 [MFC で作成したウィンドウのスタイルを変更する](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)します。

## <a name="see-also"></a>関連項目

[フレーム ウィンドウ クラス](../mfc/frame-window-classes.md)<br/>
[MFC プログラムまたはコントロールのソース ファイルとヘッダー ファイル](../ide/mfc-program-or-control-source-and-header-files.md)

