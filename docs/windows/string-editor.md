---
title: 文字列エディター (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.string.F1
helpviewer_keywords:
- String editor
- string tables
- string tables [C++], String editor
- string editing
- string editing, string tables
- resource editors [C++], String editor
- strings [C++], editing
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
ms.openlocfilehash: add153f84259985066397b6340fb4281a11beb17
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513660"
---
# <a name="string-editor-c"></a>文字列エディター (C++)

文字列テーブルは、アプリケーションのすべての文字列の ID、値、キャプションの一覧が含まれる Windows リソースです。 たとえば、文字列テーブルにはステータス バーのプロンプトがあります。

アプリケーションの開発中、いくつかの文字列テーブルを使用できます (各言語または条件ごとに 1 つ)。 しかし、実行可能モジュールには、文字列テーブルは 1 つしかありません。 実行中のアプリケーションは、テーブルを異なる DLL に置く場合、複数の文字列テーブルを参照することができます。

文字列テーブルにより、簡単にアプリケーションを異なる言語にローカライズできるようになります。 すべての文字列が文字列テーブルにある場合、ソース コードを変更せずに、文字列 (およびその他のリソース) を変換することにより、アプリケーションをローカライズすることができます。 これは通常、ソース ファイルの各種文字列を手動で検索および置換するよりも望ましい方法です。

文字列エディターを使用して、次の作業を行えます。

- [1 つ以上の文字列を検索する](../windows/finding-a-string.md)。

- 文字列テーブルに素早く [新しいエントリを挿入する](../windows/adding-or-deleting-a-string.md) 。

- [リソース ファイルから別のリソース ファイルへの文字列の移動](../windows/moving-a-string-from-one-resource-file-to-another.md)

- [ID、Value、Caption プロパティのインプレース編集を使用し](../windows/changing-the-properties-of-a-string.md) 、変更をすぐに表示します。

- [複数の文字列の Caption プロパティの変更](../windows/changing-the-caption-property-of-multiple-strings.md)

- [文字列への書式指定文字または特殊文字の追加](../windows/adding-formatting-or-special-characters-to-a-string.md)

   > [!NOTE]
   > Windows では、空の文字列テーブルを作成することができません。 エントリなしの文字列テーブルを作成する場合、そのテーブルはリソース ファイルの保存時に自動的に削除されます。

マネージ プロジェクト (共通言語ランタイムを対象とするもの) にリソースを追加する方法についてを参照してください[Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列をプロパティに割り当てる方法については、次を参照してください。[チュートリアル: Windows フォームのローカリゼーション](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3)します。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[リソース エディター](../windows/resource-editors.md)<br/>
[文字列](https://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)<br/>
[文字列の概要](/windows/desktop/menurc/about-strings)

