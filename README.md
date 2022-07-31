# ECSでアプリを起動する。

### Amazon ECRにdockerのimageを置く。
1. Amazon ECRにリポジトリを作成する。
![01](https://user-images.githubusercontent.com/65029417/182013230-ebd1c04b-70c4-41d0-9dc8-a6df71c46a8b.png)

2. Amazon ECRに以下のコマンドを用い、ローカルのdocker imageをpushする。
![02](https://user-images.githubusercontent.com/65029417/182013250-1c829734-6b11-41d8-b4a5-1fb23700a060.png)

3. Amazon ECRにimageがpushされたことの確認。
![03](https://user-images.githubusercontent.com/65029417/182013270-4bae012e-04a5-4bab-9e09-8e443cff9ab4.png)

### ネットワーク設定
1. VPCを作成。(192.168.20.0/24の範囲のアドレスを使用。)
![04](https://user-images.githubusercontent.com/65029417/182013325-2d46ab16-236a-4f6e-9b75-876e17023a4b.png)

2. サブネットを作成。(192.168.20.0/25の範囲のアドレスを使用。)
![05](https://user-images.githubusercontent.com/65029417/182013360-d3e76fe0-c11a-4f4d-8c8b-30a96c569390.png)

3. インターネット越しに通信できるように、インターネットゲートウェイを作成。(作成したVPCと紐づける)
![06](https://user-images.githubusercontent.com/65029417/182013405-bfb1df5f-acab-4124-aac7-f8e09b6ef6d4.png)

4. ルートテーブルを作成。(インターネットゲートウェイとサブネットを紐づける。)
![07](https://user-images.githubusercontent.com/65029417/182013504-6f94c157-cc2b-43ed-b3c0-7bf6dadfeb76.png)

### ECSを使用し、アプリを起動する。
1. コンテナサービスをまとめて管理するために、ECSクラスターを作成。
![08](https://user-images.githubusercontent.com/65029417/182013711-ad632c12-a0fa-4a99-baf1-9d8e44c699b4.png)

2. コンテナをどのような設定で起動するかを定義する。(どのimageを使用してコンテナを起動するかや、コンテナのサイズ等を設定する。)
![09](https://user-images.githubusercontent.com/65029417/182013782-c9f13628-2242-4bf4-bea9-b94c58833ad7.png)

3. サービスを作成。(ECSクラスターとタスク定義を紐づける。どのネットワーク内でECSを起動するのかも定義する。)
![12](https://user-images.githubusercontent.com/65029417/182014001-bcf8a435-9897-498b-ac1d-a81a3d2dbc83.png)

4. ECSのパブリックIPアドレスからアクセスするとアプリが表示される。

![14](https://user-images.githubusercontent.com/65029417/182014053-028a2dc4-1682-40a1-a1bc-a72d0433f935.png)


