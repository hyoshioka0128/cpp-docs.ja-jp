---
title: 2.9 ディレクティブの入れ子
ms.date: 11/04/2016
ms.assetid: 6565a43c-fd2d-4366-8322-8d75e1b06600
ms.openlocfilehash: 804cafd65fde19e501b89c47925f471143d74938
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438729"
---
# <a name="29-directive-nesting"></a>2.9 ディレクティブの入れ子

ディレクティブの動的なネストは、次の規則に従う必要があります。

- A**並列**別内で動的にディレクティブ**並列**論理的に現在のスレッドのみから構成される、新しいチームが、並列処理を入れ子になっている場合を除きが有効になってを確立します。

- **の**、 **セクション** 、および **単一** ディレクティブに同じバインドを **並列** 互いの内部に入れ子にするのには許可されません。

- **重要な**ディレクティブと同じ名前を互いの内部で入れ子にすることはできません。 この制限はデッドロックを防止するための十分な注意してください。

- **の**、 **のセクションでは** 、および **単一** ディレクティブはの動的範囲で許可されていません **重要な**、 **注文**、 および **マスター** 領域ディレクティブは、バインドと同じ場合 **並列** 地域とします。

- **バリア**ディレクティブはの動的範囲で許可されていません**の**、**注文**、**セクション**、**単一**、 **マスター**、および**重要な**場合は、ディレクティブのバインドを同じリージョン**並列**地域として。

- **マスター**ディレクティブはの動的範囲で許可されていません**の**、**セクション**、および**単一**ディレクティブ場合、**マスター**ディレクティブのバインドを同じ**並列**動作共有ディレクティブとして。

- **順序付けられた**ディレクティブはの動的範囲では許可されません**重要な**場合は、ディレクティブのバインドを同じリージョン**並列**地域として。

- 並列領域外で実行されるときに、並行領域内で動的に実行されるときに許可される任意のディレクティブが許可されても。 ユーザー指定の並列領域の外側に動的に実行される、ディレクティブは、マスター スレッドのみから成るチームによって実行されます。