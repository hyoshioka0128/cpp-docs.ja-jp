---
description: '詳細情報: カスタム ビルド ステップまたはビルド イベントの出力の書式設定'
title: カスタム ビルド ステップまたはビルド イベントの出力の書式設定
ms.date: 08/27/2018
helpviewer_keywords:
- builds [C++], build events
- custom build steps [C++], output format
- events [C++], build
- build events [C++], output format
- build steps [C++], output format
- builds [C++], custom build steps
ms.assetid: 92ad3e38-24d7-4b89-90e6-5a16f5f998da
ms.openlocfilehash: c2631e3c6cbd8e66d88527ff75ff7bcac9869b4f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156425"
---
# <a name="formatting-the-output-of-a-custom-build-step-or-build-event"></a>カスタム ビルド ステップまたはビルド イベントの出力の書式設定

カスタム ビルド ステップまたはビルド イベントの出力形式が正しい場合、ユーザーには次の利点があります。

- 警告とエラーが、 **[出力]** ウィンドウにカウントされます。

- 出力が、 **[タスク一覧]** ウィンドウに表示されます。

- **[出力]** ウィンドウの出力をクリックすると、該当するトピックが表示されます。

- **[タスク一覧]** ウィンドウまたは **[出力]** ウィンドウでは、F1 キーの操作を使用できます。

出力形式は、次のとおりです。

> {<em>ファイル名</em> **(** <em>行 #</em> \[ **,** <em>列 #</em>] **)** &#124; *ツール名*} **:** \[ <em>任意のテキスト</em> ] {**エラー** &#124; **警告**} <em>コード + 数値</em> **:** <em>ローカライズ可能文字列</em> \[ <em>任意のテキスト</em> ]

この場合、

- {*a* &#124; *b*} には、*a* または *b* を選択します。

- \[<em>項目</em>] は任意の文字列またはパラメーターです。

- **太字** はリテラルを表します。

次に例を示します。

> C:\\*sourcefile.cpp*(134) : エラー C2143: 構文エラー: ';' が '}' の前にありません
>
> LINK : 致命的なエラー LNK1104: '*somelib.lib*' を開くことができません。

## <a name="see-also"></a>関連項目

[カスタム ビルド ステップとビルド イベントについて](understanding-custom-build-steps-and-build-events.md)
