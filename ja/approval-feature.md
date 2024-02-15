## Security > Secure Key Manager > コンソール使用ガイド > 承認機能

국내·외 보안 인증 심사(ISMS-P, ISO 등)에서 요구하는 안전한 암호화 키 관리 요구 사항을 충족하기 위해 사용하는 Secure Key Manager의 승인 기능에 대해 설명합니다.

**승인 기능 활성화** 방법과 승인 기능 활성화 이후 승인 관련 역할 설정과 활성화 전과 후의 차이점 그리고 **승인 과정**에 대해 알아보겠습니다.

## 承認機能の有効化
組織管理画面のガバナンス設定で承認プロセス管理設定を利用してSecure Key Managerの承認機能を有効にします。

![console-guide-29](http://static.toastoven.net/prod_kms/2023-03-28-en/console-guide-29.png)

### 承認機能役割設定
Secure Key Managerのメンバー管理から承認者(APPROVAL ADMIN)、要請者(APPROVAL MEMBER)の役割を取得して承認手続きを進めます。

![console-guide-30](http://static.toastoven.net/prod_kms/2023-03-28-en/console-guide-30.png)

### 承認機能を有効にしたときの違い
承認機能を有効にして承認者または要請者の役割を取得すると、Secure Key Managerに**承認リスト**と**キー保存場所管理**タブが追加されます。2つのタブは承認者、要請者のみアクセスできます。

![console-guide-31](http://static.toastoven.net/prod_kms/2023-03-28-en/console-guide-31.png)

承認機能を有効にすると、キー保存場所でデータを追加、修正、削除できなくなり、変更リクエストを行うと**キー保存場所管理**タブに移動します。

![console-guide-32](http://static.toastoven.net/prod_kms/2023-03-28-en/console-guide-32.png)

## 承認プロセス

### 承認リクエスト作成
承認者と要請者は、**キー保存場所管理**タブでキー保存場所ごとに変更内容を承認リクエストできます。既存のキー保存場所と似た動作で追加、修正、削除を進めます。キー、認証情報の変更状態については次のように状態に表示されます。

![console-guide-33](http://static.toastoven.net/prod_kms/2023-03-28-en/console-guide-33.png)

![console-guide-34](http://static.toastoven.net/prod_kms/2023-03-28-en/console-guide-34.png)

キー保存場所の**承認リクエスト**ボタンで承認をリクエストし、該当プロジェクトの承認リクエストは**承認リスト**タブで確認できます。

![console-guide-35](http://static.toastoven.net/prod_kms/2023-03-28-en/console-guide-35.png)

### 承認リクエストの反映
承認者は、**承認リスト**からキー保存場所の変更承認リクエストを確認し、**承認**または**拒否**を選択して反映するかどうかを決定します。

![console-guide-36](http://static.toastoven.net/prod_kms/2023-03-28-en/console-guide-36.png)

承認を押すとすぐにキー保存場所に反映されます。**キー保存場所**または**キー保存場所管理**タブで変更内容を確認できます。

![console-guide-37](http://static.toastoven.net/prod_kms/2023-03-28-en/console-guide-37.png)
