---
title: Platform::ObjectDisposedException クラス
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ObjectDisposedException
- VCCORLIB/Platform::ObjectDisposedException::ObjectDisposedException
helpviewer_keywords:
- Platform::ObjectDisposedException
ms.assetid: 68506fe4-d09c-4407-999f-1e3edb261d41
ms.openlocfilehash: 41afe11efa23a3418ec9629a3c6f5a45015e2aa2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612954"
---
# <a name="platformobjectdisposedexception-class"></a>Platform::ObjectDisposedException クラス

破棄されたオブジェクトで操作が実行されるとスローされます。

## <a name="syntax"></a>構文

```cpp
public ref class ObjectDisposedException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>Remarks

詳細については、「 [COMException](../cppcx/platform-comexception-class.md)」を参照してください。

### <a name="requirements"></a>必要条件

**クライアントがサポートされている最小:** Windows 8

**サポートされているサーバーの最小値:** Windows Server 2012

**名前空間:** Platform

**メタデータ:** platform.winmd

## <a name="see-also"></a>関連項目

[Platform::COMException クラス](../cppcx/platform-comexception-class.md)