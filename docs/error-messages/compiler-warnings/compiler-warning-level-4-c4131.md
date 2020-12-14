---
description: '詳細情報: コンパイラの警告 (レベル 4) C4131'
title: コンパイラの警告 (レベル 4) C4131
ms.date: 11/04/2016
f1_keywords:
- C4131
helpviewer_keywords:
- C4131
ms.assetid: 7903b3e1-454f-4be2-aa9b-230992f96a2d
ms.openlocfilehash: b4b54a38ad634b1cc0d444b0b6d5136b6a208626
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261789"
---
# <a name="compiler-warning-level-4-c4131"></a>コンパイラの警告 (レベル 4) C4131

'function': 旧スタイルの宣言が使われています

指定された関数の宣言は、プロトタイプ形式ではありません。

旧スタイルの関数の宣言をプロトタイプ形式に変換する必要があります。

旧スタイルの関数の宣言の例を次に示します。

```c
// C4131.c
// compile with: /W4 /c
void addrec( name, id ) // C4131 expected
char *name;
int id;
{ }
```

プロトタイプ形式の例を次に示します。

```c
void addrec( char *name, int id )
{ }
```
