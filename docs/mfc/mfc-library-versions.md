---
description: '詳細情報: MFC ライブラリのバージョン'
title: MFC ライブラリのバージョン
ms.date: 05/08/2019
helpviewer_keywords:
- class libraries [MFC], building versions
- version information [MFC], MFC library
- MFC class library
- MFC class library, building
- MFC libraries
- MFC, library versions
- libraries [MFC], versions
ms.openlocfilehash: 26d17604ec201deffd5fd2d5e843269e67e3dd07
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280587"
---
# <a name="mfc-library-versions"></a>MFC ライブラリのバージョン

MFC ライブラリは、ANSI 1 バイトおよびマルチバイト文字セット (MBCS) のコードをサポートするバージョンと、Unicode をサポートするバージョン (16LE としてエンコードされた Windows ネイティブ文字セット) で使用できます。 MFC の各バージョンは、スタティックライブラリとして、または共有 DLL として使用できます。 また、サイズが非常に大きく、これらのコントロールを必要としないアプリケーションでは、ダイアログの MFC コントロールを残す mfc スタティックライブラリのバージョンも小さくなっています。 MFC ライブラリは、x86、x64、および ARM の各プロセッサを含むサポートされているアーキテクチャのデバッグバージョンとリリースバージョンの両方で使用できます。 すべてのバージョンの MFC ライブラリを使用して、アプリケーション (.exe ファイル) と Dll の両方を作成できます。 マネージコードとのやり取り用にコンパイルされた MFC ライブラリのセットもあります。 MFC の共有 Dll には、ライブラリのバイナリ互換性を示すバージョン番号が含まれています。

## <a name="automatic-linking-of-mfc-library-versions"></a>MFC ライブラリのバージョンの自動リンク

MFC ヘッダーファイルは、ビルド環境で定義されている値に基づいて、リンクする MFC ライブラリの正しいバージョンを自動的に決定します。 MFC ヘッダーファイルは、MFC ライブラリの特定のバージョンでリンクするようにリンカーに指示するコンパイラディレクティブを追加します。

たとえば、AFX のようになります。H ヘッダーファイルは、MFC の完全な静的、限定されたスタティック、または共有 DLL バージョンにリンクするようにリンカーに指示します。ANSI/MBCS または Unicode バージョンビルド構成に応じて、デバッグまたは製品版を使用します。

```cpp
#ifndef _AFXDLL
    #ifdef _AFX_NO_MFC_CONTROLS_IN_DIALOGS
        #ifdef _DEBUG
            #pragma comment(lib, "afxnmcdd.lib")
        #else
            #pragma comment(lib, "afxnmcd.lib")
        #endif
        #pragma comment(linker, "/include:__afxNoMFCControlSupportInDialogs")
        #pragma comment(linker, "/include:__afxNoMFCControlContainerInDialogs")
    #endif
    #ifndef _UNICODE
        #ifdef _DEBUG
            #pragma comment(lib, "nafxcwd.lib")
        #else
            #pragma comment(lib, "nafxcw.lib")
        #endif
    #else
        #ifdef _DEBUG
            #pragma comment(lib, "uafxcwd.lib")
        #else
            #pragma comment(lib, "uafxcw.lib")
        #endif
    #endif
#else
    #ifndef _UNICODE
        #ifdef _DEBUG
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "d.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "d.lib")
        #else
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER ".lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER ".lib")
        #endif
    #else
        #ifdef _DEBUG
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "ud.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "ud.lib")
        #else
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "u.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "u.lib")
        #endif
    #endif
#endif
```

MFC ヘッダーファイルには、MFC ライブラリ、Win32 ライブラリ、OLE ライブラリ、サンプルから構築された OLE ライブラリ、ODBC ライブラリなど、必要なすべてのライブラリにリンクするディレクティブも含まれています。

## <a name="ansi-mbcs-and-unicode"></a>ANSI、MBCS、および Unicode

MFC ANSI/MBCS ライブラリバージョンでは、ASCII などの1バイト文字セットと、Shift + JIS などのマルチバイト文字セットがサポートされています。 MFC Unicode ライブラリのバージョンでは、16LE ワイド文字でエンコードされた形式で Unicode がサポートされています。 UTF-8 でエンコードされた Unicode をサポートするには、MFC の ANSI/MBCS ライブラリバージョンを使用します。

IDE で1バイト、マルチバイト、またはワイド文字の Unicode 文字列と文字のサポートを使用するようにプロジェクト構成を設定するには、[ **プロジェクトのプロパティ** ] ダイアログボックスを使用します。 **構成プロパティ** の  >  **[全般**] ページで、[**文字セット**] プロパティを [1 バイト文字セットを使用する] に設定し **ない** ように設定します。 **マルチバイト文字** セットを使用するためにマルチバイト文字セットを使用するようにプロパティを設定するか、 **unicode 文字セット** を使用して utf-16 としてエンコードされた unicode を使用します。

MFC プロジェクトでは、プリプロセッサシンボル unicode を使用し \_ て utf-16 ワイド文字 unicode のサポートが示され、mbcs では mbcs のサポートが示さ \_ れます。 これらのオプションはプロジェクトで相互に排他的です。

## <a name="mfc-static-library-naming-conventions"></a>MFC スタティックライブラリの名前付け規則

MFC のスタティックライブラリでは、次の名前付け規則を使用します。 ライブラリ名の形式は、

> <em>u</em>AFX<em>cd</em>。変数

次の表に示すように、文字が斜体の小文字で表示されている場合は、指定子のプレースホルダーとなります。

|指定子|値と意味|
|---------------|-------------------------|
|*u*|ANSI/MBCS (N) または Unicode (U);ダイアログ内の MFC コントロールのないバージョンでは省略|
|*c*|ダイアログ内の MFC コントロールのバージョン (CW) またはなし (NMCD)|
|*d*|デバッグまたはリリース: D = デバッグ。Release の指定子を省略します|

次の表に記載されているすべてのライブラリは、サポートされているビルドアーキテクチャ用の \ atlmfc/lib ディレクトリにあらかじめ構築されています。

|ライブラリ|説明|
|-------------|-----------------|
|NAFXCW.LIB|MFC Static-Link ライブラリ、リリースバージョン|
|NAFXCWD.LIB|MFC Static-Link ライブラリ、デバッグバージョン|
|UAFXCW.LIB|Unicode をサポートする MFC Static-Link ライブラリ、リリースバージョン|
|UAFXCWD.LIB|Unicode をサポートする MFC Static-Link ライブラリ、デバッグバージョン|
|AFXNMCD.変数|Mfc ダイアログコントロールのない MFC Static-Link ライブラリ、リリースバージョン|
|AFXNMCDD.変数|Mfc ダイアログコントロールのない MFC Static-Link ライブラリ、デバッグバージョン|

同じ基本名と .pdb 拡張子を持つデバッガーファイルは、各スタティックライブラリでも使用できます。

## <a name="mfc-shared-dll-naming-conventions"></a>MFC 共有 DLL の名前付け規則

MFC の共有 Dll も、構造化された名前付け規則に従います。 これにより、どの DLL またはライブラリを使用する必要があるかがわかりやすくなります。

MFC Dll には、バイナリの互換性を示す *バージョン* 番号が付いています。 プロジェクト内で互換性を保証するために、他のライブラリやコンパイラツールセットと同じバージョンの MFC Dll を使用します。

|[DLL]|説明|
|---------|-----------------|
|MFC の *バージョン*。DLL|MFC DLL、ANSI または MBCS リリースバージョン|
|MFC *バージョン* U.DLL|MFC DLL、Unicode リリースバージョン|
|MFC *バージョン* D.DLL|MFC DLL、ANSI または MBCS デバッグバージョン|
|MFC *バージョン* UD.DLL|MFC DLL、Unicode デバッグバージョン|
|MFCM *バージョン*。DLL|MFC DLL と Windows フォームコントロール、ANSI または MBCS リリースバージョン|
|MFCM *バージョン* U.DLL|Windows フォームコントロールを使用した MFC DLL、Unicode リリースバージョン|
|MFCM *バージョン* D.DLL|MFC DLL と Windows フォームコントロール、ANSI または MBCS デバッグバージョン|
|MFCM *バージョン* UD.DLL|Windows フォームコントロールを使用した MFC DLL、Unicode デバッグバージョン|

これらの共有 Dll を使用するアプリケーションまたは MFC 拡張 Dll を構築するために必要なインポートライブラリは、DLL と同じ基本名を持ちますが、ファイル名拡張子は .lib です。 共有 Dll を使用する場合でも、小さなスタティックライブラリをコードとリンクする必要があります。このライブラリには、MFCS *バージョン*{U} {D} .lib という名前が付けられています。

MFC の共有 DLL バージョンに動的にリンクする場合は、アプリケーションからのものであるか、MFC 拡張 DLL からのものであるかにかかわらず、対応する MFC *バージョン* を含める必要があります。製品を配置するときに、DLL または MFC の *バージョン* U.DLL ます。

アプリケーションと共に配布できる Visual C++ Dll の一覧については、「 [Microsoft Visual Studio 2017 および Microsoft Visual Studio 2017 SDK の再頒布可能コード (ユーティリティおよび BuildServer ファイルを含む)](/visualstudio/productinfo/2017-redistribution-vs) 」または「 [Visual Studio 2019 の](/visualstudio/releases/2019/redistribution)再頒布可能コード」を参照してください。

MFC での MBCS および Unicode のサポートの詳細については、「 [Unicode およびマルチバイト文字セット (mbcs) のサポート](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)」を参照してください。

## <a name="dynamic-link-library-support"></a>ダイナミックリンクライブラリのサポート

MFC と MFC 以外の実行可能ファイルの両方で使用できる Dll を作成するには、静的または共有の動的 MFC ライブラリを使用できます。 これらは、"regular Dll" または "regular MFC Dll" と呼ばれ、MFC アプリおよび MFC Dll でのみ使用できる MFC 拡張 Dll と区別されます。 Mfc スタティックライブラリを使用してビルドされた DLL は、前の参照で USRDLL と呼ばれることがあります。これは、MFC DLL プロジェクトでプリプロセッサシンボル **\_ USRDLL** が定義されるためです。 MFC の共有 Dll を使用する DLL は、プリプロセッサシンボル **\_ AFXDLL** を定義するため、以前の参照では AFXDLL と呼ばれることがあります。

MFC スタティックライブラリにリンクして DLL プロジェクトを作成する場合、MFC 共有 Dll を使用せずに DLL を配置できます。 DLL プロジェクトがインポートライブラリ MFC *バージョン* にリンクするとき。LIB または MFC *バージョン*.lib。一致する MFC 共有 DLL MFC *バージョン* を配置する必要があります。Dll または MFC の *バージョン* は、dll と共にU.DLL ます。 詳細については、「 [dll](../build/dlls-in-visual-cpp.md)」を参照してください。

## <a name="see-also"></a>関連項目

[MFC の一般的なトピック](general-mfc-topics.md)
