---
title: 'MFC ActiveX コントロール : メソッドからのエラー コードのリターン'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- SetNotSupported method, using
- errors [MFC], ActiveX control error codes
- GetNotSupported method [MFC]
- FireError method [MFC]
- SCODE, MFC ActiveX controls
- ThrowError method [MFC]
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
ms.openlocfilehash: 8c5fe88cf952337a7d070eae7a5da149a8e905bd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676487"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>MFC ActiveX コントロール : メソッドからのエラー コードのリターン

この記事では、ActiveX コントロールのメソッドからエラー コードを返す方法について説明します。

メソッド内でエラーが発生したことを示す、使用する必要があります、 [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror)メンバー関数は、パラメーターとして SCODE (状態コード) をとります。 定義済み SCODE を使用したり、独自のいずれかを定義することができます。

> [!NOTE]
>  `ThrowError` プロパティの Get または Set 内からのエラーを返すための手段としてのみ使用するものでは関数またはメソッドを自動化します。 これらは、唯一のスタックの適切な例外ハンドラーとなる時間を表示します。

定義済み SCODEs などを最も一般的なのヘルパー関数が存在[COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported)、 [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported)、および[COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).

一連の定義済みの SCODEs とカスタム SCODEs を定義する手順については、セクションを参照してください。 [、ActiveX コントロールでのエラーの処理](../mfc/mfc-activex-controls-advanced-topics.md)で ActiveX コントロール: 高度なトピックです。

コードの他の領域で例外をレポートの詳細については、次を参照してください。 [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) 」、および[、ActiveX コントロールでのエラーの処理](../mfc/mfc-activex-controls-advanced-topics.md)で ActiveX コントロール: 高度なトピックです。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)

