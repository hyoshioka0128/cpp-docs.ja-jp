---
description: '詳細情報: case (C++)'
title: case (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.case
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
ms.openlocfilehash: d851e662387425ca94cc6a03877babf011c7028b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247437"
---
# <a name="case-c"></a>case (C++)

で [switch_type](switch-type.md) 属性と共に使用 **`union`** します。

## <a name="syntax"></a>構文

```cpp
[ case(value) ]
```

#### <a name="parameters"></a>パラメーター

*value*<br/>
処理を提供する必要がある入力値。 **値** の型は、次のいずれかの型になります。

- **`int`**

- **`char`**

- `boolean`

- **`enum`**

または、このような型の識別子。

## <a name="remarks"></a>解説

**Case** C++ 属性には、 **case** MIDL 属性と同じ機能があります。 この属性は、 [switch_type](switch-type.md) 属性でのみ使用されます。

## <a name="example"></a>例

次のコードは、 **case** 属性の使用方法を示しています。

```cpp
// cpp_attr_ref_case.cpp
// compile with: /LD
#include <unknwn.h>
[export]
struct SizedValue2 {
   [switch_type(char), switch_is(kind)] union {
      [case(1), string]
          wchar_t* wval;
      [default, string]
          char* val;
   };
    char kind;
};
[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>要件

| 属性コンテキスト | 値 |
|-|-|
|**適用対象**|**`class`** またはのメンバー **`struct`**|
|**Repeatable**|いいえ|
|**必須属性**|なし|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[Typedef、Enum、Union、および Struct 属性](typedef-enum-union-and-struct-attributes.md)<br/>
[クラス属性](class-attributes.md)
