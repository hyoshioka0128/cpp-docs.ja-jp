---
title: 表示して、ActiveX コントロールの追加 ダイアログ ボックス (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.controls.activex
helpviewer_keywords:
- dialog boxes [C++], adding ActiveX controls
- ActiveX controls [C++], adding to dialog boxes
ms.assetid: e1c2e3ae-e1b0-40d3-9766-623007073856
ms.openlocfilehash: 947318fb9f628c1184398c039c9697128b09c869
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642508"
---
# <a name="viewing-and-adding-activex-controls-to-a-dialog-box-c"></a>表示して、ActiveX コントロールの追加 ダイアログ ボックス (C++)

Visual Studio では、ActiveX コントロールをダイアログ ボックスに挿入することができます。

### <a name="to-see-the-activex-controls-you-have-available"></a>使用可能な ActiveX コントロールを表示するには

1. ダイアログ エディターでダイアログ ボックスを開きます。

2. ダイアログ ボックスの本体の任意の場所を右クリックします。

3. ショートカット メニューで、 **[ActiveX コントロールの挿入]** をクリックします。

   [[ActiveX コントロールの挿入] ダイアログ ボックス](../windows/insert-activex-control-dialog-box.md) が表示され、システム上のすべての ActiveX コントロールが表示されます。 ダイアログ ボックスの下部には、ActiveX コントロール ファイルへのパスが表示されます。

### <a name="to-add-an-activex-control-to-a-dialog-box"></a>ダイアログ ボックスに ActiveX コントロールを追加するには

1. [[ActiveX コントロールの挿入] ダイアログ ボックス](../windows/insert-activex-control-dialog-box.md)で、ダイアログ ボックスに追加するコントロールを選択し、 **[OK]** をクリックします。

   コントロールがダイアログ ボックスに表示されます。このダイアログ ボックスで、他のコントロールでするのと同じように、コントロールの編集またはそのハンドラーの作成を行います。

   > [!NOTE]
   > ActiveX コントロールを [[ツールボックス] ウィンドウ](/visualstudio/ide/reference/toolbox)に追加することができます。

   > [!CAUTION]
   > システム上の ActiveX コントロールの中には、配布が法的に許可されていないものもあります。 コントロールをインストールしたソフトウェアのライセンス契約を参照するか、ソフトウェア会社に問い合わせてください。

   コントロールを配置することができます、**ツールボックス**ウィンドウを簡単にアクセスします。 詳細については、「[ツールボックス](/visualstudio/ide/reference/toolbox)」をご覧ください。

マネージ プロジェクトにリソースを追加する方法についてを参照してください[Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[ダイアログ ボックスのコントロール](../windows/controls-in-dialog-boxes.md)<br/>
[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)<br/>
[ActiveX コントロール コンテナー](../mfc/activex-control-containers.md)