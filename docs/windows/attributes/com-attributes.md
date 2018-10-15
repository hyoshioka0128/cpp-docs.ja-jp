---
title: COM 属性 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- attributes [COM]
- COM, attributes
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 83d518aded30215684970e58d2868625fb8cd0e5
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/04/2018
ms.locfileid: "48791882"
---
# <a name="com-attributes"></a>COM 属性

COM 属性は、COM の開発と .NET Framework 共通言語ランタイムによる開発のさまざまな領域をサポートするためにコードを挿入します。 領域はこれらカスタム インターフェイスの実装と既存のインターフェイスのサポートからストック プロパティ、メソッド、およびイベントをサポートする範囲。 さらに、複合デバイスと ActiveX コントロールの実装のサポートを確認できます。
  
|属性|説明|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|別のコントロールでコントロールを集計できることを示します。|
|[aggregates](aggregates.md)|コントロールがターゲット クラスを集約することを示します。|
|[coclass](coclass.md)|COM インターフェイスを実装できる COM オブジェクトを作成します。|
|[com_interface_entry](com-interface-entry-cpp.md)|COM マップには、インターフェイスのエントリを追加します。|
|[implements_category](implements-category.md)|クラスの実装されたコンポーネントのカテゴリを指定します。|
|[progid](progid.md)|コントロールの ProgID を定義します。|
|[rdx](rdx.md)|作成またはレジストリ キーを変更します。|
|[registration_script](registration-script.md)|指定した登録スクリプトを実行します。|
|[requires_category](requires-category.md)|クラスの必須コンポーネントのカテゴリを指定します。|
|[support_error_info](support-error-info.md)|ターゲット オブジェクトのエラー報告をサポートしています。|
|[synchronize](synchronize.md)|メソッドへのアクセスを同期します。|
|[スレッド処理](threading-cpp.md)|COM オブジェクトのスレッド モデルを指定します。|
|[vi_progid](vi-progid.md)|コントロールのバージョンに依存しないプログラム Id を定義します。|
  
## <a name="see-also"></a>関連項目

[グループ別の属性](attributes-by-group.md)