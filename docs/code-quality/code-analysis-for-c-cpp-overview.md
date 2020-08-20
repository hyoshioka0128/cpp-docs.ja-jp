---
title: C/C++ のコード分析の概要
ms.date: 04/28/2018
ms.topic: conceptual
helpviewer_keywords:
- annotations, code analysis
- build integration, code analysis
- C/C++ code analysis
- IDE, code analysis
- pragma directive, code analysis
- code analysis, C/C++
- code analysis tool
- command line, code analysis
- C++, code analysis
- check-in policies, code analysis
- '#pragma directives, code analysis'
- C, code analysis
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
ms.openlocfilehash: 26168e66fcb2809bc1eab68d3c8fa1ccf7495568
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2020
ms.locfileid: "79467263"
---
# <a name="code-analysis-for-cc-overview"></a>C/C++ のコード分析の概要

C/C++ コード分析ツールは、C/C++ ソースコードで発生する可能性のある欠陥に関する情報を提供します。 このツールで報告される一般的なコーディング エラーとして、バッファー オーバーラン、初期化されていないメモリ、Null ポインターの逆参照、メモリ リーク、リソース リークなどがあります。 このツールでは、 [C++ コアガイドライン](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md)に対してチェックを実行することもできます。

## <a name="ide-integrated-development-environment-integration"></a>IDE (統合開発環境) の統合

コード分析ツールは、Visual Studio IDE 内で完全に統合されています。

ビルド プロセス中は、ソース コードに対して生成された警告がエラー一覧に表示されます。 警告の原因となったソース コードに移動して、問題の原因と考えられる解決策に関する追加情報を表示できます。

## <a name="command-line-support"></a>コマンドラインのサポート

次の例に示すように、コマンドラインから分析ツールを使用することもできます。

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 バージョン15.7 以降:** CMake を含む任意のビルドシステムを使用して、コマンドラインからツールを実行できます。

## <a name="pragma-support"></a>#pragma サポート

`#pragma` ディレクティブを使用して、警告をエラーとして扱うことができます。警告を有効または無効にし、個々のコード行の警告を非表示にします。 詳細については、「[プラグマ ディレクティブと __Pragma キーワード](/cpp/preprocessor/pragma-directives-and-the-pragma-keyword)」を参照してください。

## <a name="annotation-support"></a>注釈のサポート

注釈によってコード分析の精度が向上します。 注釈には、関数のパラメーターと戻り値の型について、事前および事後の状態に関する追加情報を指定します。 詳細については、「[SAL 注釈を使って C/C++ のコード障害を減らす方法](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)」を参照してください。

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>チェックイン ポリシーの一部としての分析ツールの実行

チェックインされるすべてのソース コードが、特定のポリシーを満たしていることが必要な場合があります。 具体的には、最新のローカル ビルドのステップとして分析が実行されたことを確認する必要があります。 コード分析のチェックインポリシーを有効にする方法の詳細については、「[コード分析のチェックインポリシーの作成と使用](/visualstudio/code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies)」を参照してください。

## <a name="team-build-integration"></a>チームビルドの統合

ビルドシステムの統合された機能を使用して、Azure DevOps のビルドプロセスの手順としてコード分析ツールを実行できます。 詳細については、「[Azure Pipelines](/azure/devops/pipelines/index?view=vsts)」を参照してください。

## <a name="see-also"></a>参照

- [クイックスタート: C/C++ のコード分析](quick-start-code-analysis-for-c-cpp.md)
- [チュートリアル: C/C++コードを分析して欠陥を分析する](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [C/C++ コードの警告に対応するコードの分析](code-analysis-for-c-cpp-warnings.md)
- [C++ Core ガイドライン チェッカーの使用](using-the-cpp-core-guidelines-checkers.md)
- [C++コアガイドラインチェッカーリファレンス](code-analysis-for-cpp-corecheck.md)
- [規則セットを使用してC++実行する規則を指定する](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [コード分析ツールを使用したドライバー品質の分析](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [ドライバーの警告のコード分析](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
