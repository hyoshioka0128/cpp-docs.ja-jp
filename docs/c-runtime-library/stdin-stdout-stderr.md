---
title: stdin、stdout、stderr
ms.date: 10/23/2018
f1_keywords:
- stdin
- stderr
- stdout
helpviewer_keywords:
- stdout function
- standard output stream
- standard error stream
- stdin function
- standard input stream
- stderr function
ms.assetid: badd4735-596d-4498-857c-ec8b7e670e4c
ms.openlocfilehash: f9ed1f842bd174c2b926572856152cd69ade5a56
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328020"
---
# <a name="stdin-stdout-stderr"></a>stdin、stdout、stderr

## <a name="syntax"></a>構文

```
FILE *stdin;
FILE *stdout;
FILE *stderr;
#include <stdio.h>
```

## <a name="remarks"></a>コメント

これらは、入力、出力、エラー出力の標準ストリームです。

既定では、標準入力はキーボードから読み取られ、標準出力と標準エラーは画面に出力されます。

標準ストリームにアクセスするには、次のストリーム ポインターを使用できます。

|ポインター|ストリーム|
|-------------|------------|
|`stdin`|標準入力|
|`stdout`|標準出力|
|`stderr`|標準エラー|

これらのポインターは、関数への引数として使用できます。 [getchar](../c-runtime-library/reference/getchar-getwchar.md) や [putchar](../c-runtime-library/reference/putchar-putwchar.md) などのいくつかの関数では、`stdin` と `stdout` が自動的に使用されます。

これらのポインターは定数であり、新しい値を割り当てることはできません。 ディスク ファイルやその他のデバイスにストリームをリダイレクトするには、[freopen](../c-runtime-library/reference/freopen-wfreopen.md) 関数を使用できます。 オペレーティング システムでは、プログラムの標準入力と出力をコマンド レベルでリダイレクトすることができます。

## <a name="see-also"></a>参照

[ストリーム入出力](../c-runtime-library/stream-i-o.md)<br/>
[グローバル定数](../c-runtime-library/global-constants.md)
