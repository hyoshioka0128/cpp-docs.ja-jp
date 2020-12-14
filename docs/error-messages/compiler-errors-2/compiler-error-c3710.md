---
description: 詳細については、「コンパイラエラー C3710」を参照してください。
title: コンパイラ エラー C3710
ms.date: 11/04/2016
f1_keywords:
- C3710
helpviewer_keywords:
- C3710
ms.assetid: 18bec009-5b6f-464a-a21e-5d58a6936504
ms.openlocfilehash: 6e9e146f5ec7370043756998cd162c3e57839671
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241704"
---
# <a name="compiler-error-c3710"></a>コンパイラ エラー C3710

' function ': __hook/_unhook でイベントハンドラーを指定するための構文が正しくありません \_

[__Hook](../../cpp/hook.md)または[__unhook](../../cpp/unhook.md)でイベントハンドラーを指定する場合、ハンドラーは有効なメソッドである必要があります。

## <a name="example"></a>例

次の例では、C3710 が生成されます。

```cpp
// C3710.cpp
// compile with: /link /opt:noref
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>
#include <stdio.h>

[event_source(native)]
class CEventSrc
{
public:
    __event void event1();
};

[event_receiver(native)]
class CEventRec
{
public:
    void handler1()
    {
        printf_s("Executing handler1().\n");
    }

    void HookEvents(CEventSrc* pSrc)
    {
        __hook(&CEventSrc::event1, pSrc, 0);   // C3710
        // try the following line instead
        // __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);
    }

    void UnhookEvents(CEventSrc* pSrc)
    {
        __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1);
    }
};

int main()
{
    CEventSrc eventSrc;
    CEventRec eventRec;
    eventRec.HookEvents(&eventSrc);
    eventSrc.event1();
    eventRec.UnhookEvents(&eventSrc);
}
```
