---
title: ファイル位置エラー
ms.date: 11/04/2016
helpviewer_keywords:
- file pointers [C++], file position errors
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
ms.openlocfilehash: f8c1d5dfc6a599533ce8c1dcfa624d2595779f2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554610"
---
# <a name="file-position-errors"></a>ファイル位置エラー

**ANSI 4.9.9.1, 4.9.9.4** 失敗時に `fgetpos` または `ftell` 関数によって `errno` マクロが設定された値

`fgetpos` または `ftell` が失敗すると、`errno` は、位置が無効である場合はマニフェスト定数 `EINVAL` に設定され、ファイル番号が無効である場合は `EBADF` に設定されます。 これらの定数は、ERRNO.H で定義されています。

## <a name="see-also"></a>参照

[ライブラリ関数](../c-language/library-functions.md)
