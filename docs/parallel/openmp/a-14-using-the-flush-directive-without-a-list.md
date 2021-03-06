---
title: A.14 リストのない flush ディレクティブの使用
ms.date: 11/04/2016
ms.assetid: 9e63141a-d0c6-43a5-ac16-b0bd7c89b871
ms.openlocfilehash: 13d50a6c0a3214297e931a7738305568596c3ae4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537593"
---
# <a name="a14---using-the-flush-directive-without-a-list"></a>A.14 リストのない flush ディレクティブの使用

次の例では、(の[セクション 2.6.5](../../parallel/openmp/2-6-5-flush-directive.md) 20 ページに) 共有に影響を受けるオブジェクトを区別する、`flush`ディレクティブの影響を受けない共有オブジェクト リストのないです。

## <a name="example"></a>例

### <a name="code"></a>コード

```
// omp_flush_without_list.c
#include <omp.h>

int x, *p = &x;

void f1(int *q)
{
    *q = 1;
    #pragma omp flush
    // x, p, and *q are flushed
    //   because they are shared and accessible
    // q is not flushed because it is not shared.
}

void f2(int *q)
{
    #pragma omp barrier
    *q = 2;

    #pragma omp barrier
    // a barrier implies a flush
    // x, p, and *q are flushed
    //   because they are shared and accessible
    // q is not flushed because it is not shared.
}

int g(int n)
{
    int i = 1, j, sum = 0;
    *p = 1;

    #pragma omp parallel reduction(+: sum) num_threads(10)
    {
        f1(&j);
        // i, n and sum were not flushed
        //   because they were not accessible in f1
        // j was flushed because it was accessible
        sum += j;
        f2(&j);
        // i, n, and sum were not flushed
        //   because they were not accessible in f2
        // j was flushed because it was accessible
        sum += i + j + *p + n;
    }
    return sum;
}

int main()
{
}
```