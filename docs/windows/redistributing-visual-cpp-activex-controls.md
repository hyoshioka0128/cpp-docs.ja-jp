---
description: 詳細については、「Visual C++ ActiveX コントロールの再配布」を参照してください。
title: Visual C++ ActiveX コントロールの再配布
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], redistributing
- controls [C++], distributing
ms.assetid: eefbb7e4-d28c-4c35-98bf-d9540cfaae83
ms.openlocfilehash: 4960af93b140e883ff50f6ff81824cd9e67d44f6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247346"
---
# <a name="redistributing-visual-c-activex-controls"></a>Visual C++ ActiveX コントロールの再配布

Visual C++ 6.0 には、アプリケーションで使用できてその後再配布する ActiveX コントロールが用意されています。 このようなコントロールは Visual C++ には含まれなくなりました。 Visual C++ 6.0 のライセンス契約に基づき、Visual C++ で開発されたアプリケーションでこれらのコントロールを再配布できます。

> [!NOTE]
> Microsoft では、Visual C++ 6.0 のサポートを終了しています。

再配布可能な Visual C++ 6.0 ActiveX コントロールの一覧については、Visual C++ 6.0 プロダクト CD のディスク 1 に含まれる Common\Redist\Redist.txt を参照してください。

アプリケーションを配布するとき、ActiveX コントロールの .ocx をインストールし、登録する必要があります (Regsvr32.exe を使用)。 また、ターゲット コンピューターに次のシステム ファイルの最新版が含まれている必要があります (アスタリスクはファイルを登録する必要があることを示します)。

- Asycfilt.dll

- Comcat.dll \*

- Oleaut32.dll \*

- Olepro32.dll \*

- Stdole2.tlb

対象のシステムでこれらの DLL が利用できない場合、該当オペレーティング システムを更新するための所定のメカニズムを利用して更新する必要があります。 Windows オペレーティングシステムの最新の service pack は、からダウンロードでき [http://windowsupdate.microsoft.com](https://windowsupdate.microsoft.com) ます。

データベースに接続する ActiveX コントロールを使用するとき、ターゲット コンピューターでデータ ソース名を複製する必要もあります。 複製は、`ConfigDSN` などの関数を使用してプログラムで行うことができます。

一部の再配布可能 ActiveX コントロールでは、依存関係がさらに増えます。 Visual C++ 6.0 プロダクト CD の OS\システム フォルダーにある .ocx ファイルごとに .dep ファイルもあります。 再配布する .ocx ファイルごとに、それに対応する .dep ファイルで 1 つまたは複数の USES エントリを探してください。 ファイルが一覧表示されている場合、ファイルがターゲット コンピューターにあることを確認する必要があります。 .ocx ファイルを直接サポートする DLL はすべて登録する必要があります。 (Regsvr32.exe を成功させるには、対象のコンピューターに、まずコントロールが静的に読み込むすべての Dll が含まれている必要があります)。さらに、依存関係として示されている DLL の Visual C++ 6.0 CD の Os\System フォルダーにも、.dep ファイルが含まれている場合は、その dep ファイルでエントリを使用するかどうかを調査する必要があります。

## <a name="see-also"></a>関連項目

[Visual C++ ファイルの再配布](redistributing-visual-cpp-files.md)
