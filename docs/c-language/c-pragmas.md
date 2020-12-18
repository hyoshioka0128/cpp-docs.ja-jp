---
description: '詳細情報: C プラグマ'
title: C プラグマ
ms.date: 07/26/2020
helpviewer_keywords:
- pragmas, C/C++
ms.assetid: 3d6d36b4-d565-4632-a4cd-e39aeaded5ad
ms.openlocfilehash: 45b899dc3266390095d70e8f74f6c6e5a58fc6c4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300243"
---
# <a name="c-pragmas"></a>C プラグマ

**Microsoft 固有の仕様**

"*プラグマ*" は、コンパイル時に特定のアクションを実行するようにコンパイラに指示します。 プラグマは、コンパイラごとに異なります。 たとえば、`optimize` プラグマを使用すると、プログラムで実行する最適化を設定できます。 Microsoft C のプラグマは、次のとおりです。

:::row:::
    :::column:::
        [`alloc_text`](../preprocessor/alloc-text.md)\
        [`auto_inline`](../preprocessor/auto-inline.md)\
        [`bss_seg`](../preprocessor/bss-seg.md)\
        [`check_stack`](../preprocessor/check-stack.md)\
        [`code_seg`](../preprocessor/code-seg.md)\
        [`comment`](../preprocessor/comment-c-cpp.md)\
        [`component`](../preprocessor/component.md)\
        [`const_seg`](../preprocessor/const-seg.md)\
        [`data_seg`](../preprocessor/data-seg.md)
    :::column-end:::
    :::column:::
        [`deprecated`](../preprocessor/deprecated-c-cpp.md)\
        [`detect_mismatch`](../preprocessor/detect-mismatch.md)\
        [`fenv_access`](../preprocessor/fenv-access.md)\
        [`float_control`](../preprocessor/float-control.md)\
        [`fp_contract`](../preprocessor/fp-contract.md)\
        [`function`](../preprocessor/function-c-cpp.md)\
        [`hdrstop`](../preprocessor/hdrstop.md)\
        [`include_alias`](../preprocessor/include-alias.md)\
        [`inline_depth`](../preprocessor/inline-depth.md)
    :::column-end:::
    :::column:::
        [`inline_recursion`](../preprocessor/inline-recursion.md)\
        [`intrinsic`](../preprocessor/intrinsic.md)\
        [`make_public`](../preprocessor/make-public.md)\
        [`managed`](../preprocessor/managed-unmanaged.md)\
        [`message`](../preprocessor/message.md)\
        [`omp`](../preprocessor/omp.md)\
        [`once`](../preprocessor/once.md)\
        [`optimize`](../preprocessor/optimize.md)\
        [`pack`](../preprocessor/pack.md)
    :::column-end:::
    :::column:::
        [`pop_macro`](../preprocessor/pop-macro.md)\
        [`push_macro`](../preprocessor/push-macro.md)\
        [`region`, `endregion`](../preprocessor/region-endregion.md)\
        [`runtime_checks`](../preprocessor/runtime-checks.md)\
        [`section`](../preprocessor/section.md)\
        [`setlocale`](../preprocessor/setlocale.md)\
        [`strict_gs_check`](../preprocessor/strict-gs-check.md)\
        [`unmanaged`](../preprocessor/managed-unmanaged.md)\
        [`warning`](../preprocessor/warning.md)
    :::column-end:::
:::row-end:::

Microsoft C コンパイラのプラグマについては、「[プラグマ ディレクティブと `__Pragma` キーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)」をご覧ください。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[ソース ファイルとソース プログラム](../c-language/source-files-and-source-programs.md)
