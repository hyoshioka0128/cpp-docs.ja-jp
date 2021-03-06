---
title: 複数のアクセラレータ キー (C++) のプロパティを変更します。
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: b55c9bd6-b430-48bb-b942-0e6f21d7abf9
ms.openlocfilehash: 00c2bed34d70fa13161cbaa8968d967664c8bb0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50669002"
---
# <a name="changing-the-properties-of-multiple-accelerator-keys-c"></a>複数のアクセラレータ キー (C++) のプロパティを変更します。

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>複数のアクセラレータ キーのプロパティを変更するには

1. アイコンをダブルクリックして、アクセラレータ テーブルを開く[リソース ビュー](../windows/resource-view-window.md)します。

   > [!NOTE]
   > プロジェクトに .rc ファイルがまだ含まれていない場合は、「 [リソース スクリプト ファイルの新規作成](../windows/how-to-create-a-resource-script-file.md)」を参照してください。

2. 押しながら変更するアクセラレータ キーの選択、 **Ctrl**キーのそれぞれをクリックするとします。

3. 移動して、[プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window)し、すべて、選択したアクセラレータを共有するのに必要な値を入力します。

   > [!NOTE]
   > ブール型プロパティとして各修飾子の値が表示されます、**プロパティ**ウィンドウ。 変更した場合、[修飾子](../windows/accelerator-modifier-property.md)値、**プロパティ**ウィンドウで、アクセラレータ テーブルで、れていた、修飾子の追加として新しい修飾子が扱われます。 このため場合は、修飾子の値を設定する必要がありますすべて同じすべてのアクセラレータを共有することを確認するを設定する**修飾子**設定します。

マネージ プロジェクトにリソースを追加する方法についてを参照してください[Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[アクセラレータ テーブルの編集](../windows/editing-accelerator-tables.md)<br/>
[アクセラレータ エディター](../windows/accelerator-editor.md)