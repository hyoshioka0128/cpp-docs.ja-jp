---
description: '詳細情報: OpenMP ディレクティブ'
title: OpenMP ディレクティブ
ms.date: 03/20/2019
f1_keywords:
- OpenMP directives
- atomic
- barrier
- critical
- flush
- for
- master
- parallel
- section
- single
- threadprivate
helpviewer_keywords:
- OpenMP directives
- atomic OpenMP directive
- barrier OpenMP directive
- critical OpenMP directive
- flush OpenMP directive
- for OpenMP directive
- master OpenMP directive
- ordered OpenMP directive
- parallel OpenMP directive
- sections OpenMP directive
- single OpenMP directive
- threadprivate OpenMP directive
ms.assetid: 0562c263-344c-466d-843e-de830d918940
ms.openlocfilehash: 03730b1f5cda0972dbf86b345c6e44bdad4e949b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342401"
---
# <a name="openmp-directives"></a>OpenMP ディレクティブ

OpenMP API で使用されるディレクティブへのリンクを提供します。

Visual C++ は、次の OpenMP ディレクティブをサポートしています。

並列作業共有の場合:

|ディレクティブ|説明|
|---------|-----------|
|[対応](#parallel)|並行して複数のスレッドによって実行されるコードである並列領域を定義します。|
|[for](#for-openmp)|`for`並列領域内のループで実行される作業をスレッド間で分割します。|
|[各項](#sections-openmp)|すべてのスレッド間で分割されるコードセクションを識別します。|
|[single](#single)|では、コードのセクションを1つのスレッドで実行する必要があることを指定できます。マスタースレッドであるとは限りません。|

マスターおよび同期の場合:

|ディレクティブ|説明|
|---------|-----------|
|[master](#master)|マスタースレッドだけがプログラムのセクションを実行するように指定します。|
|[critical](#critical)|コードを一度に1つのスレッドでのみ実行することを指定します。|
|[壁](#barrier)|チーム内のすべてのスレッドを同期します。すべてのスレッドがバリアを実行するまで、すべてのスレッドはバリアを停止します。|
|[的](#atomic)|アトミックに更新されるメモリ位置を指定します。|
|[揃える](#flush-openmp)|すべてのスレッドがすべての共有オブジェクトに対して同じメモリビューを持つことを指定します。|
|[番号](#ordered-openmp-directives)|並列化されたループの下にあるコードを順次ループのように実行するように指定し `for` ます。|

データ環境の場合:

|ディレクティブ|説明|
|---------|-----------|
|[threadprivate](#threadprivate)|変数がスレッドに対してプライベートであることを指定します。|

## <a name="atomic"></a><a name="atomic"></a> 的

アトミックに更新されるメモリ位置を指定します。

```cpp
#pragma omp atomic
   expression
```

### <a name="parameters"></a>パラメーター

*式 (expression)*<br/>
2つ以上の書き込みに対して保護するメモリ位置を持つ、 *左辺* 値を持つステートメント。

### <a name="remarks"></a>解説

ディレクティブは句をサポートしてい `atomic` ません。

詳細については、「 [2.6.4 atomic コンストラクト](../2-directives.md#264-atomic-construct)」を参照してください。

### <a name="example"></a>例

```cpp
// omp_atomic.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

#define MAX 10

int main() {
   int count = 0;
   #pragma omp parallel num_threads(MAX)
   {
      #pragma omp atomic
      count++;
   }
   printf_s("Number of threads: %d\n", count);
}
```

```Output
Number of threads: 10
```

## <a name="barrier"></a><a name="barrier"></a> 壁

チーム内のすべてのスレッドを同期します。すべてのスレッドがバリアを実行するまで、すべてのスレッドはバリアを停止します。

```cpp
#pragma omp barrier
```

### <a name="remarks"></a>解説

ディレクティブは句をサポートしてい `barrier` ません。

詳細については、「 [2.6.3 バリアディレクティブ](../2-directives.md#263-barrier-directive)」を参照してください。

### <a name="example"></a>例

の使用方法のサンプルについ `barrier` ては、「 [master](#master)」を参照してください。

## <a name="critical"></a><a name="critical"></a> 致命的

コードを一度に1つのスレッドでのみ実行することを指定します。

```cpp
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>パラメーター

*name*<br/>
Optionalクリティカルコードを識別する名前。 名前はかっこで囲む必要があります。

### <a name="remarks"></a>解説

ディレクティブは句をサポートしてい `critical` ません。

詳細については、「 [2.6.2 critical コンストラクト](../2-directives.md#262-critical-construct)」を参照してください。

### <a name="example"></a>例

```cpp
// omp_critical.cpp
// compile with: /openmp
#include <omp.h>
#include <stdio.h>
#include <stdlib.h>

#define SIZE 10

int main()
{
    int i;
    int max;
    int a[SIZE];

    for (i = 0; i < SIZE; i++)
    {
        a[i] = rand();
        printf_s("%d\n", a[i]);
    }

    max = a[0];
    #pragma omp parallel for num_threads(4)
        for (i = 1; i < SIZE; i++)
        {
            if (a[i] > max)
            {
                #pragma omp critical
                {
                    // compare a[i] and max again because max
                    // could have been changed by another thread after
                    // the comparison outside the critical section
                    if (a[i] > max)
                        max = a[i];
                }
            }
        }

    printf_s("max = %d\n", max);
}
```

```Output
41
18467
6334
26500
19169
15724
11478
29358
26962
24464
max = 29358
```

## <a name="flush"></a><a name="flush-openmp"></a> 揃える

すべてのスレッドがすべての共有オブジェクトに対して同じメモリビューを持つことを指定します。

```cpp
#pragma omp flush [(var)]
```

### <a name="parameters"></a>パラメーター

*var*<br/>
Optional同期するオブジェクトを表す変数のコンマ区切りのリスト。 *Var* が指定されていない場合は、すべてのメモリがフラッシュされます。

### <a name="remarks"></a>解説

ディレクティブは句をサポートしてい `flush` ません。

詳細については、「 [2.6.5 flush ディレクティブ](../2-directives.md#265-flush-directive)」を参照してください。

### <a name="example"></a>例

```cpp
// omp_flush.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

void read(int *data) {
   printf_s("read data\n");
   *data = 1;
}

void process(int *data) {
   printf_s("process data\n");
   (*data)++;
}

int main() {
   int data;
   int flag;

   flag = 0;

   #pragma omp parallel sections num_threads(2)
   {
      #pragma omp section
      {
         printf_s("Thread %d: ", omp_get_thread_num( ));
         read(&data);
         #pragma omp flush(data)
         flag = 1;
         #pragma omp flush(flag)
         // Do more work.
      }

      #pragma omp section
      {
         while (!flag) {
            #pragma omp flush(flag)
         }
         #pragma omp flush(data)

         printf_s("Thread %d: ", omp_get_thread_num( ));
         process(&data);
         printf_s("data = %d\n", data);
      }
   }
}
```

```Output
Thread 0: read data
Thread 1: process data
data = 2
```

## <a name="for"></a>次の場合は <a name="for-openmp"></a>: 

`for`並列領域内のループで実行される作業をスレッド間で分割します。

```cpp
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>パラメーター

*条項*<br/>
Optional0個以上の句、「 **解説** 」を参照してください。

*for_statement*<br/>
`for`ループ。 ループ内のユーザーコードによってインデックス変数が変更されると、未定義の動作が発生 `for` します。

### <a name="remarks"></a>解説

ディレクティブは、 `for` 次の句をサポートしています。

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [番号](openmp-clauses.md#ordered-openmp-clauses)
- [schedule](openmp-clauses.md#schedule)
- [nowait](openmp-clauses.md#nowait)

`parallel`が指定されている場合、 `clauses` は、またはディレクティブで許可されている任意の句にすることができ `parallel` `for` ます (を除く) `nowait` 。

詳細については、「 [2.4.1 for コンストラクト](../2-directives.md#241-for-construct)」を参照してください。

### <a name="example"></a>例

```cpp
// omp_for.cpp
// compile with: /openmp
#include <stdio.h>
#include <math.h>
#include <omp.h>

#define NUM_THREADS 4
#define NUM_START 1
#define NUM_END 10

int main() {
   int i, nRet = 0, nSum = 0, nStart = NUM_START, nEnd = NUM_END;
   int nThreads = 0, nTmp = nStart + nEnd;
   unsigned uTmp = (unsigned((abs(nStart - nEnd) + 1)) *
                               unsigned(abs(nTmp))) / 2;
   int nSumCalc = uTmp;

   if (nTmp < 0)
      nSumCalc = -nSumCalc;

   omp_set_num_threads(NUM_THREADS);

   #pragma omp parallel default(none) private(i) shared(nSum, nThreads, nStart, nEnd)
   {
      #pragma omp master
      nThreads = omp_get_num_threads();

      #pragma omp for
      for (i=nStart; i<=nEnd; ++i) {
            #pragma omp atomic
            nSum += i;
      }
   }

   if  (nThreads == NUM_THREADS) {
      printf_s("%d OpenMP threads were used.\n", NUM_THREADS);
      nRet = 0;
   }
   else {
      printf_s("Expected %d OpenMP threads, but %d were used.\n",
               NUM_THREADS, nThreads);
      nRet = 1;
   }

   if (nSum != nSumCalc) {
      printf_s("The sum of %d through %d should be %d, "
               "but %d was reported!\n",
               NUM_START, NUM_END, nSumCalc, nSum);
      nRet = 1;
   }
   else
      printf_s("The sum of %d through %d is %d\n",
               NUM_START, NUM_END, nSum);
}
```

```Output
4 OpenMP threads were used.
The sum of 1 through 10 is 55
```

## <a name="master"></a><a name="master"></a> マスタード

マスタースレッドだけがプログラムのセクションを実行するように指定します。

```cpp
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>解説

ディレクティブは句をサポートしてい `master` ません。

[単一](#single)のディレクティブを使用すると、コードのセクションを1つのスレッドで実行するように指定できますが、必ずしもマスタースレッドである必要はありません。

詳細については、「 [2.6.1 マスターコンストラクト](../2-directives.md#261-master-construct)」を参照してください。

### <a name="example"></a>例

```cpp
// omp_master.cpp
// compile with: /openmp
#include <omp.h>
#include <stdio.h>

int main( )
{
    int a[5], i;

    #pragma omp parallel
    {
        // Perform some computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] = i * i;

        // Print intermediate results.
        #pragma omp master
            for (i = 0; i < 5; i++)
                printf_s("a[%d] = %d\n", i, a[i]);

        // Wait.
        #pragma omp barrier

        // Continue with the computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] += i;
    }
}
```

```Output
a[0] = 0
a[1] = 1
a[2] = 4
a[3] = 9
a[4] = 16
```

## <a name="ordered"></a><a name="ordered-openmp-directives"></a> 番号

並列化されたループの下にあるコードを順次ループのように実行するように指定し `for` ます。

```cpp
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>解説

`ordered`ディレクティブは、句が指定された[for](#for-openmp)またはコンストラクトの動的な範囲内である必要があり `parallel for` `ordered` ます。

ディレクティブは句をサポートしてい `ordered` ません。

詳細については、「 [2.6.6 ordered ordered コンストラクト](../2-directives.md#266-ordered-construct)」を参照してください。

### <a name="example"></a>例

```cpp
// omp_ordered.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

static float a[1000], b[1000], c[1000];

void test(int first, int last)
{
    #pragma omp for schedule(static) ordered
    for (int i = first; i <= last; ++i) {
        // Do something here.
        if (i % 2)
        {
            #pragma omp ordered
            printf_s("test() iteration %d\n", i);
        }
    }
}

void test2(int iter)
{
    #pragma omp ordered
    printf_s("test2() iteration %d\n", iter);
}

int main( )
{
    int i;
    #pragma omp parallel
    {
        test(1, 8);
        #pragma omp for ordered
        for (i = 0 ; i < 5 ; i++)
            test2(i);
    }
}
```

```Output
test() iteration 1
test() iteration 3
test() iteration 5
test() iteration 7
test2() iteration 0
test2() iteration 1
test2() iteration 2
test2() iteration 3
test2() iteration 4
```

## <a name="parallel"></a><a name="parallel"></a> 対応

並行して複数のスレッドによって実行されるコードである並列領域を定義します。

```cpp
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>パラメーター

*条項*<br/>
Optional0個以上の句、「 **解説** 」を参照してください。

### <a name="remarks"></a>解説

ディレクティブは、 `parallel` 次の句をサポートしています。

- [if](openmp-clauses.md#if-openmp)
- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [default](openmp-clauses.md#default-openmp)
- [共用](openmp-clauses.md#shared-openmp)
- [copyin](openmp-clauses.md#copyin)
- [reduction](openmp-clauses.md#reduction)
- [num_threads](openmp-clauses.md#num-threads)

`parallel` は、 [for](#for-openmp) [セクションおよび sections](#sections-openmp) ディレクティブと共に使用することもできます。

詳細については、「 [2.3 parallel コンストラクト](../2-directives.md#23-parallel-construct)」を参照してください。

### <a name="example"></a>例

次のサンプルは、スレッドの数を設定し、並列領域を定義する方法を示しています。 スレッド数は、既定ではコンピューター上の論理プロセッサの数と同じになります。 たとえば、ハイパースレッディングが有効になっている1台の物理プロセッサを搭載したマシンでは、2つの論理プロセッサと2つのスレッドがあります。 出力の順序は、コンピューターによって異なる場合があります。

```cpp
// omp_parallel.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(4)
   {
      int i = omp_get_thread_num();
      printf_s("Hello from thread %d\n", i);
   }
}
```

```Output
Hello from thread 0
Hello from thread 1
Hello from thread 2
Hello from thread 3
```

## <a name="sections"></a><a name="sections-openmp"></a> 各項

すべてのスレッド間で分割されるコードセクションを識別します。

```cpp
#pragma omp [parallel] sections [clauses]
{
   #pragma omp section
   {
      code_block
   }
}
```

### <a name="parameters"></a>パラメーター

*条項*<br/>
Optional0個以上の句、「 **解説** 」を参照してください。

### <a name="remarks"></a>解説

`sections`ディレクティブには、0個以上のディレクティブを含めることができ `section` ます。

ディレクティブは、 `sections` 次の句をサポートしています。

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [nowait](openmp-clauses.md#nowait)

`parallel`が指定されている場合、 `clauses` は、またはディレクティブで許可されている任意の句にすることができ `parallel` `sections` ます (を除く) `nowait` 。

詳細については、「 [2.4.2 sections コンストラクト](../2-directives.md#242-sections-construct)」を参照してください。

### <a name="example"></a>例

```cpp
// omp_sections.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
    #pragma omp parallel sections num_threads(4)
    {
        printf_s("Hello from thread %d\n", omp_get_thread_num());
        #pragma omp section
        printf_s("Hello from thread %d\n", omp_get_thread_num());
    }
}
```

```Output
Hello from thread 0
Hello from thread 0
```

## <a name="single"></a><a name="single"></a> 1

では、コードのセクションを1つのスレッドで実行する必要があることを指定できます。マスタースレッドであるとは限りません。

```cpp
#pragma omp single [clauses]
{
   code_block
}
```

### <a name="parameters"></a>パラメーター

*条項*<br/>
Optional0個以上の句、「 **解説** 」を参照してください。

### <a name="remarks"></a>解説

ディレクティブは、 `single` 次の句をサポートしています。

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [copyprivate](openmp-clauses.md#copyprivate)
- [nowait](openmp-clauses.md#nowait)

[Master](#master)ディレクティブを使用すると、コードのセクションをマスタースレッドでのみ実行するように指定できます。

詳細については、「 [2.4.3 single construct](../2-directives.md#243-single-construct)」を参照してください。

### <a name="example"></a>例

```cpp
// omp_single.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(2)
   {
      #pragma omp single
      // Only a single thread can read the input.
      printf_s("read input\n");

      // Multiple threads in the team compute the results.
      printf_s("compute results\n");

      #pragma omp single
      // Only a single thread can write the output.
      printf_s("write output\n");
    }
}
```

```Output
read input
compute results
compute results
write output
```

## <a name="threadprivate"></a><a name="threadprivate"></a> threadprivate

変数がスレッドに対してプライベートであることを指定します。

```cpp
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>パラメーター

*var*<br/>
スレッドに対してプライベートにする変数のコンマ区切りのリスト。 *var* は、グローバルまたは名前空間スコープの変数またはローカルの静的変数のいずれかである必要があります。

### <a name="remarks"></a>解説

ディレクティブは句をサポートしてい `threadprivate` ません。

`threadprivate`ディレクティブは、 [__declspec](../../../cpp/declspec.md)キーワードを使用して[thread](../../../cpp/thread.md)属性に基づいてい `__declspec(thread)` ます。に適用する制限 `threadprivate` 。 たとえば、変数は、 `threadprivate` 並列領域によって生成されるスレッドチームの一部であるスレッドだけでなく、プロセスで開始されたスレッドにも存在します。 この実装の詳細に注意してください。場合によっては、ユーザー定義型のコンストラクターがより頻繁に呼び出されることに注意して `threadprivate` ください。

`threadprivate`プロセスの起動時に静的に読み込まれる dll でを使用することはできますが、 `threadprivate` [/DELAYLOAD (遅延読み込みのインポート)](../../../build/reference/delayload-delay-load-import.md)で読み込まれる dll など、 [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw)を使用して読み込む dll ではを使用できません `LoadLibrary` 。

`threadprivate`*破棄可能な* 型の変数は、というデストラクターを持つことが保証されていません。 次に例を示します。

```cpp
struct MyType
{
    ~MyType();
};

MyType threaded_var;
#pragma omp threadprivate(threaded_var)
int main()
{
    #pragma omp parallel
    {}
}
```

並列領域を作成するスレッドが終了するタイミングは、ユーザーが制御できません。 プロセスが終了したときにこれらのスレッドが存在する場合、スレッドにはプロセスの終了が通知されず、が終了したスレッド以外のスレッドでは、デストラクターは呼び出されません (ここでは、 `threaded_var` プライマリスレッド)。 したがって、コードは変数の適切な破棄をカウントしないで `threadprivate` ください。

詳細については、「 [2.7.1 threadprivate ディレクティブ](../2-directives.md#271-threadprivate-directive)」を参照してください。

### <a name="example"></a>例

の使用例については `threadprivate` 、「 [private](openmp-clauses.md#private-openmp)」を参照してください。
