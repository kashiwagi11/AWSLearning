# Amazon ECS 入門ハンズオンメモ

- ハンズオン URL：
  [Amazon ECS 入門ハンズオン](https://catalog.us-east-1.prod.workshops.aws/workshops/7ffc4ed9-d4b3-44dc-bade-676162b427cd/ja-JP)

- 今回作成した環境
  ![今回作成した環境](https://static.us-east-1.prod.workshops.aws/public/6f2ab827-2883-4f3f-ae31-63d20ce94521/static/assets/image-20220522130555288.png)

## 学習の流れ

1. AWSCloud9 で docker コンテナを作成する
2. ECR にコンテナイメージを保存する
3. ECS で保存したコンテナイメージを稼働させる

## 1. AWSCloud9 で docker コンテナを作成する

AWS Cloud9 はブラウザ上で実行できる IDE。  
Linux サーバー上で稼働しており、docker も標準でインストールされているため、コンテナイメージの作成がすぐに行える。  
Dockerfile というコンテイメージの作成命令をまとめたファイルを作成し、これを元にビルドして作成する。

- Dockerfile の指定内容

> os : ubuntu  
> webserver : apache2  
> 初期ページ : index.html(helloworld)  
> ポート : 80  
> apache の実行 shell : run_apache.sh

### docker コマンド

- docker バージョンの確認

```
docker version
```

- 現在作成されているコンテナイメージの確認

```
docker images
```

- コンテナイメージの作成

```
docker build -t <タグ名> .
```

- 実行中のコンテナ確認

```
docker ps
```

- コンテナ実行

```
docker run -d -p 8080:80 --name <コンテナ名> <タグ名>
```

- コンテナで shell 実行

```
docker exec -i -t <コンテナ名> bash
```

## 2. ECR にコンテナイメージを保存する

ECR は AWS Cloud9 の環境上で作成したコンテナイメージを保管できるレジストリ。  
保管分けするため、リポジトリを作成し、選択したリポジトリ内に保管する。  
保管したコンテナへの URI が生成されるので、使用する際はこの URI に紐づけて使用することになる。

## 3. ECS で保存したコンテナイメージを稼働させる

ECS はコンテナを動作させるためのサービス。  
使用には、まずクラスターというコンテナを動作させるための環境を指定する単位を作成する。  
このクラスターでどの VPC 環境でコンテナを実行させるかを指定する。

<br>

次に、タスク定義を作成する。  
これはコンテナの動作について定義するもので、使用するコンテナの指定、OS や CPU、メモリなどの実行環境を指定できる。

<br>

最後にサービスを作成する。  
これはクラスターとタスクを指定して、実行させるためのサービスとなる。  
ロードバランサーや維持タスク数の指定が出来るため、障害発生時に自動で対応可能となる。  
サービスにパブリック IP が割り当てられるため、外部ネットワークからコンテナにアクセスすることができる。
