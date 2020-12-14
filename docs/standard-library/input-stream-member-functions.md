---
description: '詳細情報: 入力ストリームのメンバー関数'
title: 入力ストリームのメンバー関数
ms.date: 07/19/2019
helpviewer_keywords:
- input stream objects
- input streams, member functions
ms.assetid: b4b9465d-0da9-4ccf-859d-72a68418982e
ms.openlocfilehash: 8b75470d39e5c376da497f721c725eaad8424b3d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231603"
---
# <a name="input-stream-member-functions"></a>入力ストリームのメンバー関数

入力ストリームのメンバー関数は、ディスク入力に使用します。

## <a name="open"></a><a name="vclrftheopenfunctionforinputstreamsanchor11"></a> 開き

入力ファイルストリーム () を使用している場合は `ifstream` 、そのストリームを特定のディスクファイルに関連付ける必要があります。 コンストラクターでこれを行うことも、関数を使用することもでき `open` ます。 いずれの場合も、引数は同じです。

通常、入力ストリームに関連付けられているファイルを開くときに、 [ios_base:: openmode](../standard-library/ios-base-class.md#openmode) フラグを指定します (既定のモードはです `ios::in` )。 フラグの一覧につい `openmode` ては、「 [ios_base:: openmode](../standard-library/ios-base-class.md#openmode)」を参照してください。 フラグは、ビットごとの OR ( &#124; ) 演算子と組み合わせることができます。

ファイルを読み取るには、まず、 `fail` メンバー関数を使用して、存在するかどうかを確認します。

```cpp
istream ifile("FILENAME");

if (ifile.fail())
// The file does not exist ...
```

## <a name="get"></a><a name="vclrfthegetfunctionanchor12"></a> 取得

書式設定されて `get` いないメンバー関数は、 `>>` 2 つの例外を持つ演算子のように動作します。 まず、関数には `get` 空白文字が含まれていますが、抽出機能では、フラグが設定されている場合 (既定)、空白は除外され `skipws` ます。 次に、 `get` 関数は、関連付けられた出力ストリーム (など) がフラッシュされる可能性が低くなり `cout` ます。

関数のバリエーションでは、 `get` バッファーアドレスと読み取る最大文字数を指定します。 これは、次の例のように、特定の変数に送信される文字数を制限する場合に役立ちます。

```cpp
// ioo_get_function.cpp
// compile with: /EHsc
// Type up to 24 characters and a terminating character.
// Any remaining characters can be extracted later.
#include <iostream>
using namespace std;

int main()
{
   char line[25];
   cout << " Type a line terminated by carriage return\n>";
   cin.get( line, 25 );
   cout << line << endl;
}
```

### <a name="input"></a>入力

```Input
1234
```

### <a name="sample-output"></a>サンプル出力

```Output
1234
```

## <a name="getline"></a><a name="vclrfthegetlinefunctionanchor13"></a> getline

この `getline` メンバー関数は、関数に似てい `get` ます。 両方の関数で、入力の終端文字を指定する 3 番目の引数を使用できます。 既定値は改行文字です。 両方の関数は、必須の終端文字用に 1 つの文字を予約します。 ただし、は、 `get` 終端文字をストリームに残し、 `getline` 終端文字を削除します。

次の例では、入力ストリームの終端文字を指定します。

```cpp
// getline_func.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char line[100];
   cout << " Type a line terminated by 't'" << endl;
   cin.getline( line, 100, 't' );
   cout << line;
}
```

### <a name="input"></a>入力

```Input
test
```

## <a name="read"></a><a name="vclrfthereadfunctionanchor14"></a> 込ん

この `read` メンバー関数は、ファイルから指定されたメモリ領域にバイトを読み取ります。 length 引数は、読み取られるバイト数を決定します。 この引数を含めないと、ファイルの物理的な末尾に達した場合、またはテキストモードのファイルでは埋め込まれた `EOF` 文字が読み取られた場合に、読み取りが停止します。

この例では、給与ファイルからのバイナリ レコードを構造体に読み取ります。

```cpp
#include <fstream>
#include <iostream>
using namespace std;

int main()
{
   struct
   {
      double salary;
      char name[23];
   } employee;

   ifstream is( "payroll" );
   if( is ) {  // ios::operator void*()
      is.read( (char *) &employee, sizeof( employee ) );
      cout << employee.name << ' ' << employee.salary << endl;
   }
   else {
      cout << "ERROR: Cannot open file 'payroll'." << endl;
   }
}
```

このプログラムでは、データレコードが、終端の復帰や改行文字を含まない構造体で指定されたとおりに書式設定されていることを前提としています。

## <a name="seekg-and-tellg"></a><a name="vclrftheseekgandtellgfunctionsanchor7"></a> kg と tellg

入力ファイル ストリームは、データを次に読み取るファイル内の位置を指す内部ポインターを保持します。 次に示すように、`seekg` 関数を使用してこのポインターを設定します。

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main( )
{
   char ch;

   ifstream tfile( "payroll" );
   if( tfile ) {
      tfile.seekg( 8 );        // Seek 8 bytes in (past salary)
      while ( tfile.good() ) { // EOF or failure stops the reading
         tfile.get( ch );
         if( !ch ) break;      // quit on null
         cout << ch;
      }
   }
   else {
      cout << "ERROR: Cannot open file 'payroll'." << endl;
   }
}
```

を使用し `seekg` てレコード指向のデータ管理システムを実装するには、固定長のレコードサイズをレコード番号で乗算して、ファイルの末尾を基準としたバイト位置を取得します。次に、オブジェクトを使用して `get` レコードを読み取ります。

`tellg` メンバー関数は、読み取るファイルの現在の位置を返します。 この値の型は `streampos` で、 **`typedef`** で定義されて \<iostream> います。 次の例では、ファイルを読み取り、スペースの位置を示すメッセージを表示します。

```cpp
#include <fstream>
#include <iostream>
using namespace std;

int main( )
{
   char ch;
   ifstream tfile( "payroll" );
   if( tfile ) {
       while ( tfile.good( ) ) {
          streampos here = tfile.tellg();
          tfile.get( ch );
          if ( ch == ' ' )
             cout << "\nPosition " << here << " is a space";
       }
   }
   else {
      cout << "ERROR: Cannot open file 'payroll'." << endl;
   }
}
```

## <a name="close"></a><a name="vclrftheclosefunctionforinputstreamsanchor15"></a> ok

この `close` メンバー関数は、入力ファイルストリームに関連付けられているディスクファイルを閉じ、オペレーティングシステムのファイルハンドルを解放します。 デストラクターによって [`ifstream`](../standard-library/basic-ifstream-class.md) ファイルが閉じられますが、 `close` 同じストリームオブジェクトの別のファイルを開く必要がある場合は、関数を使用できます。

## <a name="see-also"></a>関連項目

[入力ストリーム](../standard-library/input-streams.md)
