---
title: 遅延読み込みした DLL の明示的なアンロード
ms.date: 11/04/2016
helpviewer_keywords:
- /DELAY:UNLOAD linker option
- DELAY:UNLOAD linker option
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 1c4c5172-fd06-45d3-9e4f-f12343176b3c
ms.openlocfilehash: a433c9987d665aeeb910edbadac692ba9c286e3f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605388"
---
# <a name="explicitly-unloading-a-delay-loaded-dll"></a>遅延読み込みした DLL の明示的なアンロード

[/Delay](../../build/reference/delay-delay-load-import-settings.md): アンロード リンカー オプションでは、遅延読み込みされた DLL をアンロードできます。 既定で、コードが DLL をアンロード (/delay:unload を使用してと **__FUnloadDelayLoadedDLL2**)、インポート アドレス テーブル (IAT) のままに、遅延読み込みしたインポートします。 ただし、/delay:unload リンカーのコマンドラインを使用する場合、ヘルパー関数がサポート、元の形式に iat を介したをリセットする DLL の明示的なアンロード無効になったポインターが上書きされます。 IAT は内のフィールド、 [ImgDelayDescr](../../build/reference/calling-conventions-parameters-and-return-type.md) (存在する) 場合、元の IAT のコピーのアドレスを格納します。

## <a name="example"></a>例

### <a name="code"></a>コード

```
// link with /link /DELAYLOAD:MyDLL.dll /DELAY:UNLOAD
#include <windows.h>
#include <delayimp.h>
#include "MyDll.h"
#include <stdio.h>

#pragma comment(lib, "delayimp")
#pragma comment(lib, "MyDll")
int main()
{
    BOOL TestReturn;
    // MyDLL.DLL will load at this point
    fnMyDll();

    //MyDLL.dll will unload at this point
    TestReturn = __FUnloadDelayLoadedDLL2("MyDll.dll");

    if (TestReturn)
        printf_s("\nDLL was unloaded");
    else
        printf_s("\nDLL was not unloaded");
}
```

### <a name="comments"></a>コメント

遅延読み込みした DLL のアンロードで重要な注意事項:

- 実装を見つけることができます、 **__FUnloadDelayLoadedDLL2**ファイル内の関数 \VC7\INCLUDE\DELAYHLP します。CPP します。

- Name パラメーター、 **__FUnloadDelayLoadedDLL2**関数が正確に一致 (ケース) を含むどのようなインポート ライブラリが含まれています (つまり文字列は、イメージのインポート テーブル内にも)。 インポート ライブラリの内容を表示する[DUMPBIN/DEPENDENTS](../../build/reference/dependents.md)します。 大文字の文字列の一致が必要な場合は更新できます **__FUnloadDelayLoadedDLL2** CRT の文字列関数、または Windows API の呼び出しのいずれかを使用します。

参照してください[アンロード、「](../../build/reference/unloading-a-delay-loaded-dll.md)詳細についてはします。

## <a name="see-also"></a>関連項目

[リンカーによる DLL の遅延読み込み](../../build/reference/linker-support-for-delay-loaded-dlls.md)