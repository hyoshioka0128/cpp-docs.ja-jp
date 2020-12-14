---
description: '詳細情報: 致命的なエラー C1900'
title: 致命的なエラー C1900
ms.date: 11/04/2016
f1_keywords:
- C1900
helpviewer_keywords:
- C1900
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
ms.openlocfilehash: e7bcd44846f34b3d3910d4c1aac292ee6414b439
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276115"
---
# <a name="fatal-error-c1900"></a>致命的なエラー C1900

> '*Tool1*' バージョン '*number1*' と '*tool2*' バージョン '*number2*' が一致しません。

コンパイラのさまざまなパスで実行されたツールが一致しません。 *number1* と *number2* は、ファイルの日付を表します。 たとえば、パス 1 ではコンパイラ フロントエンドが (c1.dll) を実行し、パス 2 ではコンパイラ バックエンドが (c2.dll) を実行します。 ファイルの日付が一致する必要があります。

この問題を解決するには、Visual Studio のすべての更新プログラムが適用されたことを確認します。 問題が引き続き発生する場合は、Windows コントロールパネルの [ **プログラムと機能** ] を使用して、Visual Studio を修復または再インストールします。
