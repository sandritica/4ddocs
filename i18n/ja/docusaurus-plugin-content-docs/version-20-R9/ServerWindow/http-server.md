---
id: http-server
title: HTTPサーバーページ
---

**HTTPサーバー** ページには、4D Server の Webサーバーや SOAPサーバーに関する情報が集められています。 Webサーバーは、HTMLページやピクチャーなどの Webコンテンツの公開を可能にします。 SOAPサーバーは Webサービスの公開を管理します。 これら 2つのサーバーは、4D Server の内部的な HTTPサーバーに依存しています。

![](../assets/en/Admin/server-admin-web-page.png)

ページの上部には、4D Server の HTTPサーバーの現在の状況が表示されます。

- **状況**: 開始または停止
- **開始時刻**: HTTPサーバーの起動日と時刻。
- **動作時間**: HTTPサーバーが最後に開始されてからの経過時間。
- **総HTTPヒット数**: HTTPサーバーが開始されてから、サーバーが受信したローレベルの HTTPヒット数。

## HTTPサーバー開始/停止

このボタンは切り替え表示され、4D Server HTTPサーバーをコントロールするために使用します。

- HTTPサーバーの状態が "開始" の場合、ボタンのタイトルは **HTTPサーバー停止** になります。 このボタンをクリックすると、4D Server HTTPサーバーは即座に停止し、Webサーバー、RESTサーバー、および SOAPサーバーはリクエストを受け付けなくなります。
- HTTPサーバーの状態が "停止" の場合、ボタンのタイトルは **HTTPサーバー開始** になります。 このボタンをクリックすると、4D Server HTTPサーバーは即座に開始し、Web、REST、および SOAPリクエストを受け付けます。

> HTTPサーバーを開始するには適切なライセンスが必要です。
>
> ストラクチャー設定で設定してアプリケーション起動と同時に、またはプログラムを使用して必要な時に、HTTPサーバーを自動で開始することができます。

## Web情報

このエリアには、4D Server の Webサーバーに関する情報が表示されます。

- **Web リクエスト**: 受け入れ、または拒否。 この情報は Webサーバーが有効かどうかを示します。 Webサーバーは直接 HTTPサーバーにリンクしているため、HTTPサーバーが開始されていれば Webリクエストは受信され、停止されていれば拒否されます。
- **最大接続数**: 許可される Web接続の最大数。 この値は、サーバーマシンにインストールされているライセンスによります。

## SOAP情報

このエリアには、4D Server の SOAPサーバーに関する情報が表示され、コントロールボタンも一つ含まれます。

- **SOAP リクエスト**: 受け入れ、または拒否。 この情報は SOAPサーバーが有効かどうかを示します。 SOAPリクエストを受け入れるためには、HTTPサーバーが開始され、かつ SOAPサーバーが明示的にリクエストを受け入れなければなりません (ボタンの説明参照)。
- **最大接続数**: 許可される SOAP接続の最大数。 この値は、サーバーマシンにインストールされているライセンスによります。
- **SOAPリクエストを受け入れる/受け入れない** ボタン: このボタンは切り替え表示され、4D Server SOAPサーバーのコントロールに使用します。 このボタンをクリックすると、ストラクチャー設定の "Webサービス" ページの **Webサービスリクエストを許可する** オプションが変更されます。 また、[`SOAP REJECT NEW REQUESTS`](../commands-legacy/soap-reject-new-requests.md) コマンドを使って新規の SOAPリクエストを拒否することもできますが、このコマンドは **Webサービスリクエストを許可する** オプションの値を変更しません。

HTTPサーバー停止中に **SOAPリクエスト受け入れる** ボタンをクリックすると、4D は自動で HTTPサーバーを開始します。

## HTTPサーバー設定

このエリアには、HTTPサーバーの設定パラメーターや動作に関する情報が表示されます。

- **開始時に自動起動**: ストラクチャー設定で設定されたパラメーター。
- **HTTP サーバープロセス (使用/総計)**: サーバー上で作成されたHTTPプロセス数 (現在のプロセス数 / 作成されたプロセスの総数)。
- **キャッシュメモリ**: HTTPサーバーキャッシュメモリのサイズ ( キャッシュが実際に使用しているサイズ / ストラクチャー設定で理論的にキャッシュに割り当てられた最大サイズ)。 **キャッシュクリア** ボタンをクリックすると、現在のキャッシュを空にすることができます。
- **待受IP**、**HTTPポート** (デフォルトは 80)、HTTP接続用の **TSL有効** (4D と SQL接続は別設定)、および **HTTPSポート**: これらは、ストラクチャー設定またはプログラミングにより設定された、HTTPサーバーの現在の [設定パラメーター](WebServer/webServerConfig.md) を表示します。
- **ログファイル情報**: 名称、フォーマット、および HTTPサーバーの次回の自動ログバックアップの日付 (logweb.txt ファイル)。

