---
description: '詳細情報: ベストプラクティスと例 (SAL)'
title: ベスト プラクティスと例 (SAL)
ms.date: 11/04/2016
ms.topic: conceptual
ms.openlocfilehash: d252f019637aa65aacb0bcfd7e924d94bda0d400
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97279599"
---
# <a name="best-practices-and-examples-sal"></a>ベスト プラクティスと例 (SAL)

ここでは、ソースコード注釈言語 (SAL) を最大限に活用し、いくつかの一般的な問題を回避する方法をいくつか紹介します。

## <a name="_in_"></a>\_含まれる\_

関数が要素に書き込むことが想定されている場合は、の代わりにを使用し `_Inout_` `_In_` ます。 これは、古いマクロから SAL への自動変換の場合に特に関連します。 SAL より前は、多くのプログラマはマクロをコメントとして使用していました `IN` `OUT` `IN_OUT` 。このような名前のマクロは、、、、またはこれらの名前のバリアントでした。 これらのマクロを SAL に変換することをお勧めしますが、元のプロトタイプが記述された後にコードが変更されている可能性があり、古いマクロがコードの動作を反映しなくなる可能性があるため、変換する際には注意が必要です。 コメントマクロについては特に注意して `OPTIONAL` ください。たとえば、コンマの間違った側など、誤って配置されることがよくあります。

```cpp

// Incorrect
void Func1(_In_ int *p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}

// Correct
void Func2(_Inout_ PCHAR p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}
```

## <a name="_opt_"></a>\_opt\_

呼び出し元が null ポインターを渡すことが許可されていない場合は、 `_In_` またはの代わりにまたはを使用し `_Out_` `_In_opt_` `_Out_opt_` ます。 これは、パラメーターをチェックする関数に対しても適用され、でない場合は NULL である場合はエラーを返します。 関数によってパラメーターが予期しない NULL としてチェックされ、正常に返されるのは、適切な防御コーディング手法であるということではありませんが、パラメーター注釈を省略可能な型 () にすることはできません `_*Xxx*_opt_` 。

```cpp

// Incorrect
void Func1(_Out_opt_ int *p1)
{
    *p = 1;
}

// Correct
void Func2(_Out_ int *p1)
{
    *p = 1;
}
```

## <a name="_pre_defensive_-and-_post_defensive_"></a>\_\_防御前 \_ と \_ \_ 防御後\_

関数が信頼境界にある場合は、注釈を使用することをお勧め `_Pre_defensive_` します。  "防御" 修飾子は、呼び出しの時点で、インターフェイスを厳密に確認する必要があることを示すために、特定の注釈を変更します。ただし、実装本文では、正しくないパラメーターが渡される可能性があると想定する必要があります。 この場合、 `_In_ _Pre_defensive_` は信頼境界で推奨されます。これは、呼び出し元が null を渡そうとするとエラーが発生し、関数本体は null である可能性があるかのように解析され、最初に null をチェックせずにポインターを参照解除しようとすると、フラグが設定されます。  `_Post_defensive_`注釈は、信頼できるパーティが呼び出し元であると見なされ、信頼されていないコードが呼び出されたコードであるコールバックで使用することもできます。

## <a name="_out_writes_"></a>\_出力の \_ 書き込み\_

次の例は、の一般的な誤用を示して `_Out_writes_` います。

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);
```

注釈は、 `_Out_writes_` バッファーがあることを示します。 `cb`最初のバイトが終了時に初期化されたバイトが割り当てられています。 この注釈は厳密には間違っていないため、割り当てられたサイズを表すと便利です。 ただし、関数によって初期化される要素の数はわかりません。

次の例では、バッファーの初期化された部分の正確なサイズを完全に指定するための3つの正しい方法を示します。

```cpp

// Correct
void Func1(_Out_writes_to_(size, *pCount) CHAR *pb,
    DWORD size,
    PDWORD pCount
);

void Func2(_Out_writes_all_(size) CHAR *pb,
    DWORD size
);

void Func3(_Out_writes_(size) PSTR pb,
    DWORD size
);
```

## <a name="_out_-pstr"></a>\_Out \_ pstr

の使用 `_Out_ PSTR` は、ほぼ常に間違っています。 これは、文字バッファーを指す出力パラメーターがあり、それが NULL で終わると解釈されます。

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);
```

のような注釈は、 `_In_ PCSTR` 一般的で便利です。 の前提条件では、 `_In_` null で終わる文字列を認識できるため、null 終了を含む入力文字列を指します。

## <a name="_in_-wchar-p"></a>\_\_WCHAR * p 内

`_In_ WCHAR* p` 1つの文字を指す入力ポインターがあることを示し `p` ます。 ただし、ほとんどの場合、これは意図した仕様ではない可能性があります。 代わりに、NULL で終わる配列の指定が想定されています。これを行うには、を使用 `_In_ PWSTR` します。

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);
```

NULL 終了の適切な指定が一般的ではありません。 次の例に示すように、適切なバージョンを使用し `STR` て型を置き換えます。

```cpp

// Incorrect
BOOL StrEquals1(_In_ PCHAR p1, _In_ PCHAR p2)
{
    return strcmp(p1, p2) == 0;
}

// Correct
BOOL StrEquals2(_In_ PSTR p1, _In_ PSTR p2)
{
    return strcmp(p1, p2) == 0;
}
```

## <a name="_out_range_"></a>\_\_範囲外\_

パラメーターがポインターであり、ポインターによってポイントされている要素の値の範囲を表す場合は、の代わりにを使用し `_Deref_out_range_` `_Out_range_` ます。 次の例では、* pcbFilled つぶしの範囲を指定しています。 pcbFilled つぶされていません。

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Out_range_(0, cbSize) DWORD *pcbFilled
);

// Correct
void Func2(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Deref_out_range_(0, cbSize) _Out_ DWORD *pcbFilled
);
```

`_Deref_out_range_(0, cbSize)` は、から推論できるため、一部のツールでは厳密には必須ではありません `_Out_writes_to_(cbSize,*pcbFilled)` が、完全を期すためにここに示します。

## <a name="wrong-context-in-_when_"></a>When のコンテキストが正しくありません \_\_

もう1つの一般的な誤りは、事前条件の事後評価を使用することです。 次の例で `_Requires_lock_held_` は、は前提条件です。

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);
```

式が、 `result` 事前状態では使用できない状態の後の値を参照しています。

## <a name="true-in-_success_"></a>成功した場合は TRUE \_\_

戻り値が0以外の場合に関数が成功した場合は、では `return != 0` なく成功条件としてを使用し `return == TRUE` ます。 0以外のは、コンパイラがに対して提供する実際の値と等価であるとは限りません `TRUE` 。 のパラメーターは `_Success_` 式で、次の式は等価として評価されます。 `return != 0` 、、 `return != false` 、およびは、 `return != FALSE` `return` パラメーターも比較もありません。

```cpp
// Incorrect
_Success_(return == TRUE) _Acquires_lock_(*lpCriticalSection)
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);

// Correct
_Success_(return != 0) _Acquires_lock_(*lpCriticalSection)
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);
```

## <a name="reference-variable"></a>参照変数

参照変数の場合、以前のバージョンの SAL では、暗黙的なポインターを注釈のターゲットとして使用し、 `__deref` 参照変数に関連付けられている注釈にを追加する必要があります。 このバージョンはオブジェクト自体を使用するため、追加のを必要としません `_Deref_` 。

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Deref_ _Out_range_(0, 2) _Out_ DWORD &cbSize
);

// Correct
void Func2(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Out_range_(0, 2) _Out_ DWORD &cbSize
);
```

## <a name="annotations-on-return-values"></a>戻り値に関する注釈

次の例は、戻り値の注釈における一般的な問題を示しています。

```cpp

// Incorrect
_Out_opt_ void *MightReturnNullPtr1();

// Correct
_Ret_maybenull_ void *MightReturnNullPtr2();
```

この例では、は、 `_Out_opt_` 前提条件の一部としてポインターが NULL である可能性があることを示しています。 ただし、事前条件を戻り値に適用することはできません。 この場合、正しい注釈は `_Ret_maybenull_` です。

## <a name="see-also"></a>関連項目

[C/C++ コードの欠陥を減らすための SAL 注釈の使用](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)  
[SAL について](../code-quality/understanding-sal.md)  
[関数パラメーターおよび戻り値の注釈設定](../code-quality/annotating-function-parameters-and-return-values.md)  
[関数の動作に注釈を付ける](../code-quality/annotating-function-behavior.md)  
[構造体とクラスに注釈を付ける](../code-quality/annotating-structs-and-classes.md)  
[ロック動作に注釈を付ける](../code-quality/annotating-locking-behavior.md)  
[注釈を適用するタイミングと場所の指定](../code-quality/specifying-when-and-where-an-annotation-applies.md)  
[組み込み関数](../code-quality/intrinsic-functions.md)
