---
description: '詳細については、「方法: System:: Guid と _GUID を変換する」を参照してください。'
title: '方法: System::Guid と _GUID の間で変換を行う'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- System::GUID
- GUID, converting to System::GUID
- System::GUID, converting to GUID
ms.assetid: 022c934c-3395-4f04-b498-85ad9bf8c646
ms.openlocfilehash: 1f2eb87f23e7f47221b4506c2c9e328803b800e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304390"
---
# <a name="how-to-convert-between-systemguid-and-_guid"></a>方法: System::Guid と _GUID の間で変換を行う

次のコードサンプルは、との間で変換を行う方法を示して <xref:System.Guid> `_GUID` います。

## <a name="example"></a>例

```cpp
// convert_guids.cpp
// compile with: /clr
#include <windows.h>
#include <stdio.h>

using namespace System;

Guid FromGUID( _GUID& guid ) {
   return Guid( guid.Data1, guid.Data2, guid.Data3,
                guid.Data4[ 0 ], guid.Data4[ 1 ],
                guid.Data4[ 2 ], guid.Data4[ 3 ],
                guid.Data4[ 4 ], guid.Data4[ 5 ],
                guid.Data4[ 6 ], guid.Data4[ 7 ] );
}

_GUID ToGUID( Guid& guid ) {
   array<Byte>^ guidData = guid.ToByteArray();
   pin_ptr<Byte> data = &(guidData[ 0 ]);

   return *(_GUID *)data;
}

int main() {
   _GUID ng = {0x11111111,0x2222,0x3333,0x44,0x55,0x55,0x55,0x55,0x55,0x55,0x55};
   Guid mg;

   Console::WriteLine( (mg = FromGUID( ng )).ToString() );
   _GUID ng2 = ToGUID( mg );

   printf_s(  "%x-%x-%x-", ng2.Data1, ng2.Data2, ng2.Data3 );
   for (int i = 0 ; i < 8 ; i++) {
      if (i == 2)
         printf_s("-");
      printf_s("%x", ng2.Data4[i]);
   }
   printf_s("\n");
}
```

```Output
11111111-2222-3333-4455-555555555555
11111111-2222-3333-4455-555555555555
```

## <a name="see-also"></a>関連項目

[C++ Interop (暗黙の PInvoke) の使用](../dotnet/using-cpp-interop-implicit-pinvoke.md)
