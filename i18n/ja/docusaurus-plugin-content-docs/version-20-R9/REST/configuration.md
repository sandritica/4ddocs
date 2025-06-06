---
id: configuration
title: サーバー設定
---

4D の RESTサーバーは、標準の HTTPリクエストを用いて外部アプリケーションがアプリケーションのデータにアクセスすることを可能にします。つまり、プロジェクトのデータクラス情報を取得したり、データを操作したり、Webアプリケーションにログインしたり、といったことが可能です。

REST機能を使い始めるまえに、まずは 4D REST サーバーの設定をおこない、これを起動させる必要があります。

## RESTサーバーを開始する

セキュリティ上の理由により、デフォルトでは、4D は RESTリクエストに応答しません。 RESTサーバーを開始し、RESTリクエストを処理するには、**ストラクチャー設定** の **Web** ＞ **Web機能** ページにて、**RESTサーバーとして公開** オプションを有効化する必要があります。

![alt-text](../assets/en/REST/Settings.png)

> RESTサービスは 4D の HTTPサーバーを使用するため、4D Webサーバーが開始されていることを確認してください。

このオプションが有効化されると、「警告: アクセス権が正しく設定されているか確認してください。」という警告メッセージが表示されます。これは REST接続の認証設定がされていない限り、デフォルトではデータベースオブジェクトに自由にアクセスできてしまうためです。

> 変更を反映するには、4Dアプリケーションを再起動する必要があります。

## RESTアクセスの制御

デフォルトでは、REST接続はすべてのユーザーに対してオープンですが、この状態はライセンス管理上もセキュリティ上も推奨されません。

As of 4D 20 R6, you configure REST accesses by enabling the [**force login** mode](authUsers.md#force-login-mode) and create an [`authentify()`](authUsers.md#function-authentify) datastore class function to authenticate users and assign privileges to their web session.

:::note 互換性

The **Access** area in the Settings dialog box is only available in converted projects for compatibility. See [Access](../settings/web.md#access) for more information.

:::

## テーブルやフィールドの公開

4Dアプリケーションの RESTサービスが有効化されると、[データストアインターフェース](ORDA/dsMapping.md#データストア) を通して 4Dデータベースのすべてのテーブルとフィールドおよび格納データが RESTセッションによってデフォルトでアクセス可能です。 つまり、すべてのデータにアクセス可能ということです。 たとえば、データベースに [Employee] テーブルが含まれている場合、次のように書くことができます:

```
http://127.0.0.1:8044/rest/Employee/?$filter="salary>10000"

```

このリクエストで、salary (給与) フィールドが 10000以上の社員データが取得されます。

> "非表示" 属性を選択されたテーブルやフィールドも、デフォルトで REST に公開されています。

REST 経由でアクセス可能なデータストアオブジェクトを制限するには、アクセス不可にするテーブルやフィールドについて "RESTリソースとして公開" オプションを選択解除する必要があります。 許可されていないリソースへの RESTリクエストがあった場合、4Dはエラーを返します。

### テーブルの公開

デフォルトでは、すべてのテーブルが REST に公開されています。

セキュリティ上の理由から、データベースの一部のテーブルのみを公開したい状況もあるでしょう。 たとえば、[Users] テーブルを作成し、その中にユーザー名とパスワードが保存されている場合、そのテーブルは公開しない方が賢明でしょう。

テーブルを公開したくない場合は:

1. ストラクチャーエディターにて対象となるテーブルを選択し、右クリックでコンテキストメニューを開いてテーブルプロパティを選択します。

2. **RESTリソースとして公開** オプションの選択を解除します:
    ![alt-text](../assets/en/REST/table.png)
    公開設定を変更する各テーブルに対して、この手順を繰り返します。

### フィールドの公開

デフォルトでは、すべての 4Dデータベースフィールドが REST に公開されています。

テーブルの一部のフィールドのみを非公開にしたい状況もあるでしょう。 たとえば、[Employees]Salary のようなフィールドは非公開の方がよいでしょう。

フィールドを非公開にするには:

1. ストラクチャーエディターにて対象となるフィールドを選択し、右クリックでコンテキストメニューを開いてフィールドプロパティを選択します。

2. フィールドの **RESTリソースとして公開** オプションの選択を解除します:
    ![alt-text](../assets/en/REST/field.png)
    Repeat this for each field whose exposure needs to be modified.

> あるフィールドが REST を通してアクセス可能であるためには、その親テーブルも公開されている必要があります。 親テーブルが公開されていない場合、各フィールドの公開設定に関わらず、すべてのフィールドがアクセス不可になります。

## プリエンプティブモード

4D Server上では、**インタプリタモードであっても**、RESTリクエストは自動的にプリエンプティブプロセスで処理されます。 そのため、コードは [プリエンプティブ実行に準拠](../WebServer/preemptiveWeb.md#スレッドセーフなWebサーバーコードの書き方) している必要があります。

> To debug interpreted web code on the server machine, make sure the debugger is [attached to the server](../Debugging/debugging-remote.md) or [to a remote machine](../Debugging/debugging-remote.md). これにより、Webプロセスがコオペラティブモードに切り替わり、Webサーバーコードのデバッグが可能になります。

シングルユーザーの 4D では、インタープリターコードは常にコオペラティブモードで実行されます。
