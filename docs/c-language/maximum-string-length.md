---
description: '詳細情報: 最大文字列長'
title: 最大文字列長
ms.date: 11/04/2016
helpviewer_keywords:
- lengths, strings
- string length, maximum
- maximum string length
- strings [C++], length
ms.assetid: 99a80e4a-6212-47b7-a6bd-bdf99bd44928
ms.openlocfilehash: 1da7618a044be2427bd0b0f7f4931287ee4b8014
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243433"
---
# <a name="maximum-string-length"></a>最大文字列長

**Microsoft 固有の仕様**

ANSI 互換性は、コンパイラが連結の後に文字列リテラルを 509 文字まで受け入れるように要求します。 Microsoft C で使用できる文字列リテラルの最大長は約 2,048 バイトです。 ただし、文字列リテラルが二重引用符で囲まれた複数の部分で構成されている場合、プリプロセッサはそれらの部分を単一の文字列に連結し、連結された各行に対して合計バイト数に 1 バイトを追加します。

たとえば、1 行あたり 50 文字の 40 行 (2,000 文字) の文字列と、7 文字で構成される 1 行があり、各行は二重引用符で囲まれているとします。 この場合、2,007 バイトと終端の null 文字の 1 バイトを加算し、合計 2,008 バイトとなります。 連結後は、最初の各 40 行に余分な文字が追加されています。 そのため、合計は 2,048 バイトになります。 行連結文字 (\\) が二重引用符の代わりに使用されている場合、プリプロセッサは各行に余分な文字を追加しません。

引用符で囲まれた個々の文字列が 2048 バイトを超えることはできませんが、文字列を連結することで、ほぼ 65535 バイトの文字列リテラルを作成できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[C 文字列リテラル](../c-language/c-string-literals.md)
