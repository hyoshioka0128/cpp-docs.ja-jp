---
description: '詳細については、次を参照してください: first_is'
title: first_is (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.first_is
helpviewer_keywords:
- first_is attribute
ms.assetid: 89acbf56-3b38-4d44-83e8-1ce2f6f74ffd
ms.openlocfilehash: 151a9defdde078a062f000860ebb40c3d1c9b466
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236270"
---
# <a name="first_is"></a>first_is

転送される最初の配列要素のインデックスを指定します。

## <a name="syntax"></a>構文

```cpp
[ first_is("expression") ]
```

### <a name="parameters"></a>パラメーター

*式 (expression)*<br/>
1つ以上の C 言語式。 空の引数スロットが許可されます。

## <a name="remarks"></a>解説

**First_is** C++ 属性には、 [first_is](/windows/win32/Midl/first-is) MIDL 属性と同じ機能があります。

## <a name="example"></a>例

次のコードは、配列内のセクションを指定するさまざまな方法を示しています。

```cpp
// cpp_attr_ref_first_is.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"

[module(name="MyLib")];

[object, uuid(11111111-1111-1111-1111-111111111111)]
__interface b
{
   [id(0), propget, bindable, displaybind, defaultbind,
requestedit] HRESULT get_I([out, retval]long *i);
   HRESULT Proc1([in] short First, [in] short Last,
[first_is(First), last_is(Last), size_is(Last-First)] char Arr1[]);
   HRESULT Proc2([in] short First, [in] short Last,
[last_is(First), size_is(Last)] char Arr2[]);
};
```

## <a name="requirements"></a>要件

| 属性コンテキスト | 値 |
|-|-|
|**適用対象**|**`struct`** またはのフィールド **`union`** 、インターフェイスパラメーター、インターフェイスメソッド|
|**Repeatable**|いいえ|
|**必須属性**|なし|
|**無効な属性**|なし|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[Typedef、Enum、Union、および Struct 属性](typedef-enum-union-and-struct-attributes.md)<br/>
[パラメーター属性](parameter-attributes.md)<br/>
[last_is](last-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)
