---
description: '詳細情報: 一次式の識別子'
title: 一次式の識別子
ms.date: 11/04/2016
helpviewer_keywords:
- identifiers, designating objects
ms.assetid: d4602fe6-e7e6-40cc-9823-3b1ebf5d3d38
ms.openlocfilehash: 63fbadeb786edda232282a5073dd85b22f487e9b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182178"
---
# <a name="identifiers-in-primary-expressions"></a>一次式の識別子

識別子は、整数、 **`float`** 、 **`enum`** 、 **`struct`** 、 **`union`** 、配列、ポインター、または関数型を持つことができます。 識別子は、オブジェクトの指定として宣言された場合 (その場合は左辺値)、または関数として宣言された場合 (その場合は関数指定子) の一次式です。 左辺値の定義については、「[左辺値と右辺値の式](../c-language/l-value-and-r-value-expressions.md)」を参照してください。

配列識別子によって表されるポインター値は変数ではないので、配列識別子は、代入演算の左オペランドを形成することができず、したがって変更可能な左辺値ではありません。

関数として宣言される識別子は、値が関数のアドレスであるポインターを表します。 ポインターは、指定された型の値を返す関数をアドレス指定します。 したがって、関数識別子は代入演算子の左辺値にすることもできません。 詳細については、[識別子](../c-language/c-identifiers.md)に関するページを参照してください。

## <a name="see-also"></a>関連項目

[C 一次式](../c-language/c-primary-expressions.md)
