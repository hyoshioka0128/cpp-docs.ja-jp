---
title: '変換: 診断'
ms.date: 11/04/2016
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
ms.openlocfilehash: 4863b97dc1db7ff295b5f786ca97da2551d0fa62
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664998"
---
# <a name="translation-diagnostics"></a>変換: 診断

**ANSI 2.1.1.3** 診断を識別する方法

Microsoft C は、次の形式のエラー メッセージを生成します。

> *filename* **(** *line-number* **) :** *diagnostic* **C**<em>number</em> *message*

ここで、*filename* はエラーが発生したソース ファイルの名前、*line-number* はコンパイラがエラーを検出した行番号、*diagnostic* は "error" または "warning"、*number* は (構文に示すように先頭に **C** が付いた) 一意の 4 桁の番号、*message* は説明メッセージです。

## <a name="see-also"></a>参照

[実装で定義された動作](../c-language/implementation-defined-behavior.md)