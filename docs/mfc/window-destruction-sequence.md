---
title: ウィンドウの破棄順序
ms.date: 11/04/2016
helpviewer_keywords:
- destruction, windows
- destroying windows
- sequence [MFC], window destruction
- CWnd objects [MFC], destruction sequence
- sequence [MFC]
- windows [MFC], destroying
ms.assetid: 2d819196-6240-415f-a308-db43745e616c
ms.openlocfilehash: 07312d6c7bba219cebcfa2c73a8d66c9c97ec08e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571354"
---
# <a name="window-destruction-sequence"></a>ウィンドウの破棄順序

ユーザーがウィンドウの既定値であるフレーム ウィンドウを閉じるときに、MFC フレームワーク[OnClose](../mfc/reference/cwnd-class.md#onclose)ハンドラー呼び出し[DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)します。 Windows のウィンドウが破棄されるときに呼び出されます最後のメンバー関数は[OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy)、呼び出しを行ういくつかのクリーンアップ、[既定](../mfc/reference/cwnd-class.md#default)メンバーが Windows のクリーンアップを実行する関数を呼び出す最後に、仮想メンバー関数[PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)します。 [CFrameWnd](../mfc/reference/cframewnd-class.md)の実装`PostNcDestroy`C++ ウィンドウ オブジェクトを削除します。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [割り当てとウィンドウ メモリの解放](../mfc/allocating-and-deallocating-window-memory.md)

- [Cwnd と HWND の分離](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>関連項目

[ウィンドウ オブジェクトの破棄](../mfc/destroying-window-objects.md)

