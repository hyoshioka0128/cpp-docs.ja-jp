---
title: ガイドの設定 ダイアログ ボックス (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- DLUs (dialog units)
- Dialog Editor [C++], snap to guides
- grid spacing
- guides, settings
- dialog units (DLUs)
- layout grid in Dialog Editor
- snap to guides (Dialog editor)
- controls [C++], snap to guides/grid
- Guide Settings dialog box (Dialog editor)
ms.assetid: 55381e1c-146a-4fa7-b1b3-b1492817615f
ms.openlocfilehash: 2f83acddf0f56225f74961ef31988a5938685b67
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483617"
---
# <a name="guide-settings-dialog-box-c"></a>ガイドの設定 ダイアログ ボックス (C++)

## <a name="layout-guides"></a>レイアウト ガイド

レイアウト ガイドの設定を表示します。

### <a name="none"></a>なし

レイアウト ツールを非表示にします。

### <a name="rulers-and-guides"></a>ルーラーとガイド

有効な場合は、レイアウト ツールにルーラーを追加します。ガイドは、ルーラーに配置することができます。 既定のガイドは、余白は、ドラッグして移動することができます。 ガイドを配置するルーラーをクリックします。 ガイドの上または横に、コントロールが移動したときに「スナップ」を制御します。 これには、アタッチすると、コントロールは、ガイドにも移動します。 コントロールがそれぞれの側では、ガイドにアタッチされているし、ガイドを移動、コントロールのサイズします。

### <a name="grid"></a>グリッド

レイアウト グリッドを作成します。 新しいコントロールがグリッドに自動的に整列します。

## <a name="grid-spacing"></a>グリッド間隔

ダイアログ ボックスの単位 (Dlu) では、グリッドの間隔の設定を表示します。

### <a name="width-dlus"></a>幅: Dlu

Dlu でレイアウト グリッドの幅を設定します。 水平 DLU は、4、ダイアログ ボックスのフォントの平均幅です。

### <a name="height-dlus"></a>Height: Dlu

Dlu でレイアウト グリッドの高さを設定します。 垂直 DLU は 8 で割った値 ダイアログ ボックスのフォントの高さの平均値です。

マネージ プロジェクトにリソースを追加する方法についてを参照してください[Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[レイアウト グリッドの変更](../windows/modifying-the-layout-grid.md)<br/>
[ダイアログ エディターの状態 (ガイドとグリッド)](../windows/dialog-editor-states-guides-and-grids.md)