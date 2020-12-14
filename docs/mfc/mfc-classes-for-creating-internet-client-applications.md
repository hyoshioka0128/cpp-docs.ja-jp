---
description: 詳細については、「インターネットクライアントアプリケーションを作成するための MFC クラス」を参照してください。
title: インターネット クライアント アプリケーションの作成用の MFC クラス
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, WinInet classes
- WinInet classes [MFC], classes
- classes [MFC], MFC
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
ms.assetid: 67d34117-9839-4f4b-8bb8-0e4a9471c606
ms.openlocfilehash: c68110182b01d9c425090a926ee1e352ca3d3bdf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280678"
---
# <a name="mfc-classes-for-creating-internet-client-applications"></a>インターネット クライアント アプリケーションの作成用の MFC クラス

MFC には、インターネットクライアントアプリケーションを作成するための次のクラスとグローバル関数が用意されています。 インデントは、クラスがその上のインデントされクラスから派生したことを示します。 `CGopherFile` とは `CHttpFile` `CInternetFile` 、たとえば、から派生します。 これらのクラスとグローバル関数は、AFXINET.H で宣言されています。H。ただし `CFileFind` 、AFX で宣言されています。

## <a name="classes"></a>クラス

- [CInternetSession](reference/cinternetsession-class.md)

- [CInternetConnection](reference/cinternetconnection-class.md)

  - [CFtpConnection](reference/cftpconnection-class.md)

  - [CGopherConnection](reference/cgopherconnection-class.md)

  - [CHttpConnection](reference/chttpconnection-class.md)

- [CInternetFile](reference/cinternetfile-class.md)

  - [CGopherFile](reference/cgopherfile-class.md)

  - [CHttpFile](reference/chttpfile-class.md)

- [CFileFind](reference/cfilefind-class.md)

  - [CFtpFileFind](reference/cftpfilefind-class.md)

  - [CGopherFileFind](reference/cgopherfilefind-class.md)

- [CGopherLocator](reference/cgopherlocator-class.md)

- [CInternetException](reference/cinternetexception-class.md)

## <a name="global-functions"></a>グローバル関数

- [AfxParseURL](reference/internet-url-parsing-globals.md#afxparseurl)

- [AfxGetInternetHandleType](reference/internet-url-parsing-globals.md#afxgetinternethandletype)

- [AfxThrowInternetException](reference/internet-url-parsing-globals.md#afxthrowinternetexception)

## <a name="see-also"></a>関連項目

[Win32 インターネット拡張機能 (WinInet)](win32-internet-extensions-wininet.md)<br/>
[インターネットクライアントクラスの前提条件](prerequisites-for-internet-client-classes.md)<br/>
[MFC WinInet クラスを使用したインターネットクライアントアプリケーションの作成](writing-an-internet-client-application-using-mfc-wininet-classes.md)
