---
title: CObject から新しくクラスを派生する必要性
ms.date: 11/04/2016
f1_keywords:
- CObject
helpviewer_keywords:
- derived classes [MFC], from CObject
- CObject class [MFC], when to use
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
ms.openlocfilehash: c2361967dcfce5e46aeec65ade3d7056b362949d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636606"
---
# <a name="do-i-have-to-derive-new-classes-from-cobject"></a>CObject から新しくクラスを派生する必要性

いいえ、ありません。

クラスを派生[CObject](../mfc/reference/cobject-class.md)がでシリアル化やダイナミック creatability などの機能を必要がある場合。 データ クラスの多くは、ため、多くの場合からも派生することをお勧めのファイルにシリアル化する必要があります`CObject`します。 派生したクラスの例の`CObject`を参照してください、 [Scribble サンプル](../visual-cpp-samples.md)します。

## <a name="see-also"></a>関連項目

[CObject クラス: Q & A 集](../mfc/cobject-class-frequently-asked-questions.md)
