---
title: オブジェクト (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.object
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
ms.openlocfilehash: 1cae9e6b014f33dfbbcccdeb4172d6f35349e307
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526164"
---
# <a name="object-c"></a>object (C++)

カスタム インターフェイスを識別します。

## <a name="syntax"></a>構文

```cpp
[object]
```

## <a name="remarks"></a>Remarks

インターフェイス定義の直前、**オブジェクト**C++ 属性により、インターフェイスのカスタム インターフェイスとして .idl ファイル内に配置されます。

オブジェクトでマークされた任意のインターフェイスを継承する必要があります`IUnknown`します。 継承する基本インターフェイスのいずれかの場合、この条件が満たされる`IUnknown`します。 基底インターフェイスを継承しない場合`IUnknown`、コンパイラでマークされたインターフェイスと、**オブジェクト**から派生する`IUnknown`します。

## <a name="example"></a>例

参照してください[nonbrowsable](nonbrowsable.md)を使用する方法の例については**オブジェクト**します。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**interface**|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[インターフェイス属性](interface-attributes.md)<br/>
[dual](dual.md)<br/>
[dispinterface](dispinterface.md)<br/>
[custom](custom-cpp.md)<br/>
[__interface](../../cpp/interface.md)