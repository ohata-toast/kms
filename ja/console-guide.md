## Security > Secure Key Manager > コンソール使用ガイド

コンソール使用ガイドでは、Secure Key Managerを使用するための基本的な内容を説明します。
- **キー保存場所の作成**
- **キーの作成**
- **認証情報の登録**
- **ユーザーデータの管理**

### キー保存場所の作成
Secure Key Managerは、キー保存場所の単位として認証情報とキーを管理します。キー保存場所がない場合は、図1のような画面が表示されます。

![console-guide-01](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-01.png)

**キー保存場所の追加**をクリックすると、図2のようにキー保存場所を作成できるウィンドウが表示されます。

![console-guide-02](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-02.png)

名前と説明を入力し、１つ以上の認証方法を選択した後、**追加**をクリックするとキー保存場所を作成します。作成したキー保存場所は図3のようにキー保存場所リストに表示されます。

![console-guide-03](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-03.png)

キー保存場所リストでキー保存場所をクリックすると、図4のようにキー保存場所を管理できるメニューが表示されます。

![console-guide-04](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-04.png)

### キーの作成
Secure Key Managerは、キーを3つのタイプに区分します。機密データは文字列データを保存し、APIを使用した照会機能を提供します。対称鍵はAPIを使用したデータ暗号化/復号機能を提供します。非対称鍵はAPIを使用したデータ署名/検証機能を提供します。ユーザーは使用目的に合ったキータイプを選択して、キーを作成できます。

**キー管理**メニューをクリックすると、図5のようにキーを管理できる画面が表示されます。

![console-guide-05](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-05.png)

キー管理画面で**キー追加**をクリックすると、キーを作成できるウィンドウが表示されます。選択したキータイプに応じて図6、図7、図8のように必要なデータを入力できます。

![console-guide-06](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-06.png)

![console-guide-07](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-07.png)

![console-guide-08](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-08.png)

機密データを選択すると名前、説明、データを入力できます。対称鍵/非対称鍵を選択すると名前、説明、更新周期を入力できます。必須データを入力した後、**追加**をクリックするとキーを作成します。作成したキーは図9のように管理画面に表示されます。

![console-guide-09](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-09.png)

### 認証情報の登録
Secure Key Managerで作成したキーは、認証に成功したクライアントでのみ使用できます。クライアントの認証に使用する認証情報は**IPv4アドレス管理**、**MACアドレス管理**、***証明書管理**メニューで登録します。

#### IPv4アドレスの登録
**IPv4アドレス管理**をクリックすると、図10のようにクライアント認証に使用するIPv4アドレス管理画面が表示されます。

![console-guide-10](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-10.png)

**IPv4アドレス追加**をクリックすると、図11のようにIPv4アドレスを追加できるウィンドウが表示されます。

![console-guide-11](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-11.png)

クライアントIPv4アドレスと説明を入力した後、**追加**をクリックするとIPv4アドレスを追加します。この時IPv4アドレスは、クライアントがSecure Key Managerに接続する時に使用するIPv4アドレスを入力する必要があります。追加したIPv4アドレスは、図12のようにIPv4アドレス管理画面に表示されます。

![console-guide-12](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-12.png)

#### MACアドレスの登録
**MACアドレス管理**をクリックすると、図13のようにクライアント認証に使用するMACアドレス管理画面が表示されます。

![console-guide-13](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-13.png)

**MACアドレス追加**をクリックすると、図14のようにMACアドレスを追加できるウィンドウが表示されます。

![console-guide-14](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-14.png)

クライアントMACアドレスと説明を入力した後、**追加**をクリックすると、MACアドレスを追加します。追加したMACアドレスは、図15のようにMACアドレス管理画面に表示されます。

![console-guide-15](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-15.png)

#### クライアント証明書の登録
**証明書管理**をクリックすると、図16のようにクライアント認証に使用する証明書管理画面が表示されます。

![console-guide-16](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-16.png)

**証明書追加**をクリックすると、図17のように証明書を作成できるウィンドウが表示されます。

![console-guide-17](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-17.png)

証明書名、パスワード、説明を入力し、使用期間を選択した後、**追加**をクリックすると証明書を作成します。作成した証明書は、図18のように証明書管理画面に表示されます。証明書管理画面で**ダウンロードアイコン**をクリックすると証明書ファイルをダウンロードします。

![console-guide-18](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-018.png)

### ユーザーデータの管理
Secure Key Managerは、ユーザーが作成したデータ(キー、認証情報)の詳細情報を提供します。図19のようなユーザーデータリストで**詳細情報アイコン**をクリックすると、図20のように詳細情報が表示されます。

![console-guide-19](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-19.png)

![console-guide-20](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-20.png)

#### ユーザーデータの削除

ユーザーが作成したデータの初期状態は**使用中**です。不要なデータを削除するには、図21のように**詳細情報**ウィンドウで**削除リクエスト**をクリックします。

![console-guide-21](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-21.png)

削除をリクエストすると、図22のようにデータ状態が**削除予定**に変更されます。**削除予定**に変更されたデータは使用することができず、7日後に完全に削除されます。

![console-guide-22](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-22.png)

**削除予定**状態のデータは、**即時削除**をクリックして削除予定時間まで待たずにすぐに削除するか、**削除キャンセル**をクリックして**使用中**状態に戻すことができます。

#### 対称鍵/非対称鍵の更新

Secure Key Managerは、対称鍵/非対称鍵の更新を提供します。図23のように対称鍵/非対称鍵詳細情報ウィンドウで自動更新周期を設定できます。更新周期を0に設定した場合は、自動更新を行いません。

![console-guide-23](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-23.png)

図24のように、更新周期に30以上の値を設定すると、次の更新日を表示し、更新周期ごとにキーを自動的に更新します。

![console-guide-24](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-24.png)

図25のように対称鍵/非対称鍵詳細情報ウィンドウで**即時更新**をクリックすると、キーをすぐに更新できます。

![console-guide-25](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-25.png)

キーを更新すると、図26のようにキーバージョンリストに新しいバージョンが追加されます。

![console-guide-26](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-26.png)
