---
title: __movsb
ms.date: 11/04/2016
f1_keywords:
- __movsb
helpviewer_keywords:
- movsb instruction
- rep movsb instruction
- __movsb intrinsic
ms.assetid: ba5469f6-f797-4cd2-bee8-74c7666c26d4
ms.openlocfilehash: 9dc32f460a2098d2a216c725f49c0389f77043c2
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51329034"
---
# <a name="movsb"></a>__movsb

**Microsoft 固有の仕様**

移動の文字列が生成されます (`rep movsb`) 命令。

## <a name="syntax"></a>構文

```
void __movsb(
   unsigned char* Destination,
   unsigned const char* Source,
   size_t Count
);
```

#### <a name="parameters"></a>パラメーター

*変換先*<br/>
[out]コピー先へのポインター。

*ソース*<br/>
[in]コピーのソースへのポインター。

*カウント*<br/>
[in]コピーするバイト数。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__movsb`|x86、x64|

**ヘッダー ファイル** \<intrin.h >

## <a name="remarks"></a>Remarks

その結果、最初の`Count`によって示されるバイト`Source`にコピーされます、`Destination`文字列。

このルーチンは、組み込みとしてのみ使用できます。

## <a name="example"></a>例

```
// movsb.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsb)

int main()
{
    unsigned char s1[100];
    unsigned char s2[100] = "A big black dog.";
    __movsb(s1, s2, 100);

    printf_s("%s %s", s1, s2);
}
```

```Output
A big black dog. A big black dog.
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)