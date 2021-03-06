---
title: データの整列
ms.date: 11/04/2016
f1_keywords:
- data.alignment
helpviewer_keywords:
- data alignment [C++]
ms.assetid: 35ac3d2d-a4b3-421b-954f-b7372b1f18e1
ms.openlocfilehash: 7d835545bdc1f94de56846f35d510927c06c2560
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520286"
---
# <a name="data-alignment"></a>データの整列

次の C ランタイム関数はデータを配置できます。

## <a name="data-alignment-routines"></a>データ配置ルーチン

|ルーチンによって返される値|使用|
|-------------|---------|
|[_aligned_free](../c-runtime-library/reference/aligned-free.md)|[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) または [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) で割り当てられたメモリ ブロックを解放します。|
|[_aligned_free_dbg](../c-runtime-library/reference/aligned-free-dbg.md)|[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) または [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) で割り当てられたメモリ ブロックを解放します (デバッグのみ)。|
|[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)|指定された配置の境界にメモリを割り当てます。|
|[_aligned_malloc_dbg](../c-runtime-library/reference/aligned-malloc-dbg.md)|デバッグ ヘッダーと上書きバッファー用の追加の領域を持つメモリを、指定された配置境界に割り当てます (デバッグ バージョンのみ)。|
|[_aligned_msize](../c-runtime-library/reference/aligned-msize.md)|ヒープで割り当てられたメモリ ブロックのサイズを返します。|
|[_aligned_msize_dbg](../c-runtime-library/reference/aligned-msize-dbg.md)|ヒープで割り当てられたメモリ ブロックのサイズを返します (デバッグ バージョンのみ)。|
|[_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md)|指定された配置の境界にメモリを割り当てます。|
|[_aligned_offset_malloc_dbg](../c-runtime-library/reference/aligned-offset-malloc-dbg.md)|指定された配置境界にメモリを割り当てます (デバッグ バージョンのみ)。|
|[_aligned_offset_realloc](../c-runtime-library/reference/aligned-offset-realloc.md)|[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) または [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) で割り当てられたメモリ ブロックのサイズを変更します。|
|[_aligned_offset_realloc_dbg](../c-runtime-library/reference/aligned-offset-realloc-dbg.md)|[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) または [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) で割り当てられたメモリ ブロックのサイズを変更します (デバッグ バージョンのみ)。|
|[_aligned_offset_recalloc](../c-runtime-library/reference/aligned-offset-recalloc.md)|[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) または [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) で割り当てられたメモリ ブロックのサイズを変更し、メモリを 0 に初期化します。|
|[_aligned_offset_recalloc_dbg](../c-runtime-library/reference/aligned-offset-recalloc-dbg.md)|[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) または [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) で割り当てられたメモリ ブロックのサイズを変更し、メモリを 0 に初期化します (デバッグ バージョンのみ)。|
|[_aligned_realloc](../c-runtime-library/reference/aligned-realloc.md)|[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) または [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) で割り当てられたメモリ ブロックのサイズを変更します。|
|[_aligned_realloc_dbg](../c-runtime-library/reference/aligned-realloc-dbg.md)|[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) または [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) で割り当てられたメモリ ブロックのサイズを変更します (デバッグ バージョンのみ)。|
|[_aligned_recalloc](../c-runtime-library/reference/aligned-recalloc.md)|[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) または [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) で割り当てられたメモリ ブロックのサイズを変更し、メモリを 0 に初期化します。|
|[_aligned_recalloc_dbg](../c-runtime-library/reference/aligned-recalloc-dbg.md)|[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) または [_aligned_offset_malloc](../c-runtime-library/reference/aligned-offset-malloc.md) で割り当てられたメモリ ブロックのサイズを変更し、メモリを 0 に初期化します (デバッグ バージョンのみ)。|

## <a name="see-also"></a>参照

[カテゴリ別ユニバーサル C ランタイム ルーチン](../c-runtime-library/run-time-routines-by-category.md)<br/>