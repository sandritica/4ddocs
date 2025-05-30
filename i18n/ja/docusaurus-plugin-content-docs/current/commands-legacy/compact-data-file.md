---
id: compact-data-file
title: Compact data file
slug: /commands/compact-data-file
displayed_sidebar: docs
---

<!--REF #_command_.Compact data file.Syntax-->**Compact data file** ( *structurePath* ; *dataPath* {; *archiveFolder* {; *option* {; *method*}}} ) : Text<!-- END REF-->
<!--REF #_command_.Compact data file.Params-->
| 引数 | 型 |  | 説明 |
| --- | --- | --- | --- |
| structurePath | Text | &#8594;  | ストラクチャーファイルのパス名 |
| dataPath | Text | &#8594;  | 圧縮するデータファイルのパス名 |
| archiveFolder | Text | &#8594;  | 元のデータファイルを置く、フォルダーのパス名 |
| option | Integer | &#8594;  | 圧縮オプション |
| method | Text | &#8594;  | 4Dコールバックメソッド名 |
| 戻り値 | Text | &#8592; | 元のデータファイルが置かれたフォルダーの完全パス名 |

<!-- END REF-->

## 説明 

<!--REF #_command_.Compact data file.Summary-->**Compact data file**コマンドは、ストラクチャー*structurePath*に関連付けられている、*dataPath* 引数で指定されたデータファイルを圧縮します。<!-- END REF-->圧縮に関する詳細は4D Design Referenceマニュアルを参照してください。

データベースの操作の継続を確かなものにするため、圧縮された新しいデータファイルが自動で元のファイルと置き換えられます。安全のため、元のファイルは変更されず、“Replaced files (compacting) YYYY-MM-DD HH-MM-SS”という特別なフォルダーに移動されます。YYYY-MM-DD HH-MM-SSはバックアップが行われた日付と時刻を表します。例えば“Replaced files (compacting) 2007-09-27 15-20-35”のようになります。

コマンドは、元のデータファイルを格納するために作成されたフォルダーの、実際の完全なパス名を返します。このコマンドはローカルモードの4D、または4D Serverのストアドプロシージャーでのみ実行できます。圧縮するデータファイルは、*structurePath*で指定するストラクチャーファイルに対応するものでなければなりません。さらにコマンド実行時にデータファイルが開かれていてはなりません。そうでなければエラーが生成されます。  
圧縮処理中にエラーが発生した場合、元のファイルは最初の場所に保持されます。インデックスファイル (.4DIndxファイル) がデータファイルに関連付けられていれば、それも圧縮されます。データファイルと同様元のファイルは保存され、新しく圧縮されたファイルと置き換えられま す。

* *structurePath* 引数には、圧縮するデータファイルに関連付けられたストラクチャーファイルの完全パス名を渡します。この情報は圧縮プロシージャーのために必要です。パス名は OSのシンタックスで表現されなければなりません。なお空の文字列を渡すと、標準のファイルを開くダイアログボックスが表示され、使用するストラクチャーファイルを選択させることができます。
* *dataPath* 引数には、空の文字列、ファイル名、またはOSのシンタックスで表現された完全パス名を渡すことができます。空の文字列を渡すと、標準のファイルを開くダイアログボックスが表示され、圧縮するデータファイルを選択させることができます。このファイルは*structurePath* 引数で指定されたストラクチャーファイルに対応するものでなければなりません。データファイル名のみを渡すと、4Dはストラクチャーファイルと同階層でデータファイルを探します。
* オプションの*archiveFolder* 引数を使用して、元のデータファイルとインデックスファイルを保存する“Replaced files (compacting) DateTime”フォルダーの場所を指定できます。  
このコマンドは、実際に作成されたこのフォルダーのパス名を返します。  
\- この引数を省略すると、元のファイルは自動で、ストラクチャーファイルと同階層に作成される“Replaced files (compacting) DateTime”フォルダーに置かれます。  
\- 空の文字列を渡すと、標準のフォルダーを開くダイアログが表示され、ユーザーは作成するフォルダーの場所を選択できます。  
\- OSのシンタックスを使用してパス名を指定すると、コマンドは指定された場所に“Replaced files (compacting) DateTime”フォルダーを作成します。
* オプションの*options* 引数を使用して、さまざまな圧縮オプションを指定できます。これを行うには*Data File Maintenance*テーマの以下の定数を使用してください。加算することで複数のオプションを指定できます:  

| 定数                      | 型    | 値      | コメント                                                                                                                                                                                                |  
| ----------------------- | ---- | ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |  
| Compact address table   | 倍長整数 | 131072 | 強制的にレコードのアドレステーブルを更新します (圧縮時間は長くなります)。このオプションのみを指定すると、4Dは自動でレコードの再保存オプションを有効にします。この場合、レコード番号が更新される点に留意してください。                                                                                       |  
| Create process          | 倍長整数 | 32768  | このオプションが渡されると圧縮は非同期で行われ、コールバックメソッドを使用して結果を管理しなければなりません。4Dは進捗状況を表示しません (コールバックメソッドを使用して表示させることができます)。プロセスが正しく起動されるとOKシステム変数が1に設定され、他の場合は0に設定されます。このオプションが渡されない時、圧縮が行われればOK変数に1が設定され、そうでなければ0が設定されます。 |  
| Do not create log file  | 倍長整数 | 16384  | 通常このコマンドはXMLフォーマットのログファイルを作成します。このオプションを使用すればログファイルは作成されません。                                                                                                                                        |  
| Timestamp log file name | 倍長整数 | 262144 | このオプションが渡された場合、生成されたログファイルの名前は作成された日時を含みます。結果として、以前に生成されていたログファイルをどれも上書きする事はありません。このオプションが渡されていなかった場合、デフォルトではログファイル名はタイムスタンプされることはなく、生成されたログファイルはそれぞれ古いものを上書きします。                                   |  
| Update records          | 倍長整数 | 65536  | 現在のストラクチャー定義に基づき、すべてのレコードを強制的に再保存します。                                                                                                                                                               |
* *method* 引数は、Create processオプションを渡したときに、圧縮中定期的に呼び出されるコールバックメソッドを指定するために使用します。このオプションが指定されていなければ、コール バックメソッドが呼び出されることはありません。このメソッドに関する詳細は、[VERIFY DATA FILE](verify-data-file.md)コマンドの説明を参照してください。

デフォルトで、Compact data fileコマンドはXMLフォーマットのログファイルを作成します (Do not create log fileオプションを指定しない場合。*options* 引数の説明を参照)。このファイルはデータベースの**Logs**フォルダーに作成され、名前もカレントデータベースのストラクチャーファイルに基づいたものがつけられます。例えば、“myDB.4db”という名前のストラクチャーファイルに対しては、ログファイルは“myDB\_Compact\_Log.xml”という名前が付けられます。  
Timestamp log file nameオプションを渡していた場合、ログファイル名には"YYYY-MM-DD HH-MM-SS"という形式で作成時の日時の情報が含まれます。ファイル名は例として次のような形になりま す:“myDB\_Compact\_Log\_2015-09-27 15-20-35.xml” これはつまりそれぞれの新しいログファイルは以前のものを置き換える事はない一方、不要なファイルを削除するためにはいくつかのファイルを手動で削除しな ければならない可能性があることを意味します。  
選択されたオプションに関わらず、ログファイルが生成されるとそのファイルへのパスはコマンド実行後に*Document*システム変数へと返されます。

## 例題 

以下の例題 (Windows) は、データファイルの圧縮を実行します:

```4d
 $structFile:=Structure file
 $dataFile:="C:\\Databases\\Invoices\\January\\Invoices.4dd"
 $origFile:="C:\\Databases\\Invoices\\Archives\\January\\"
 $archFolder:=Compact data file($structFile;$dataFile;$origFile)
```

## システム変数およびセット 

圧縮処理が正しく終了したら、OKシステム変数に１が設定されます。そうでなければ0が設定されます。ログファイルが生成されていた場合、その完全パス名がDocumentシステム変数へと返されます。

## 参照 

[Table fragmentation](table-fragmentation.md)  
[VERIFY DATA FILE](verify-data-file.md)  

## プロパティ

|  |  |
| --- | --- |
| コマンド番号 | 937 |
| スレッドセーフである | &check; |
| システム変数を更新する | OK、Document |


