# AWS - ECS Workshop - Cats and Dogs-

- ハンズオン URL：
  [ECS Workshop - Cats and Dogs-](https://dcj71ciaiav4i.cloudfront.net/D0B5A980-C9FC-11EB-ABD7-3362918AE194/)

- 今回作成した環境
  ![今回作成した環境](https://dcj71ciaiav4i.cloudfront.net/D0B5A980-C9FC-11EB-ABD7-3362918AE194/images/intro/architecture.svg)

## 今回の学習について

前回[(前回の学習メモ)](https://github.com/kashiwagi11/AWSLearning/tree/main/ECSWebApplication%E3%83%8F%E3%83%B3%E3%82%BA%E3%82%AA%E3%83%B3)、前々回[(前々回の学習メモ)](https://github.com/kashiwagi11/AWSLearning/tree/main/AmazonECS%E5%85%A5%E9%96%80%E3%83%8F%E3%83%B3%E3%82%BA%E3%82%AA%E3%83%B3)に引き続き、コンテナ関連の学習を行った。
コンテナ関連のハンズオンをコンプリートしていく勢いでやっていく。  
用語や関連ツールの使い方がなんとなくつかめてきているので、さらに慣れていくためである。

## 学習の流れ

1. Amazon CloudFormation でハンズオン環境構築
2. Amazon ECR に Docker イメージを保存
3. Amazon ECS クラスタでコンテナ管理
4. Fargate ハンズオン

## Amazon CloudFormation でハンズオン環境構築

- Amazon CloudFormation とは  
  AWS のリソース（VPC、EC2、セキュリティグループなど）をテンプレートどおりに自動作成することができる機能。  
  テンプレートは自作できるため、同じ環境構成を使いまわすことができる。

Amazon CloudFormation により、ハンズオン側で用意されているテンプレートを使って、ハンズオン環境を作成した。  
環境構築が一瞬で完了したので、早速本題に入ることができた。

## Amazon ECR に Docker イメージを保存

AWS Cloud9 で Docker イメージをビルドし、ECR にプッシュする。  
事前の環境構築で、Docker ファイルまで作成してあったので、細かい部分はあまり身につかない。  
動きの流れを体験する構成になっていると感じた。

手順を一部読み飛ばしており、EC2 に ECR 権限の IAM を付与し忘れており、ECR に接続できずに少しつまずいた。

## Amazon ECS クラスタでコンテナ管理

ECS では、コンテナが稼働する場所として、EC2 か Fargate を使用できる。
今回は EC2 と Fargate 両方で作成し、ALB で分散させる構成をとる。

作成したサンプル（すべて最初の環境構築で用意されている）サイトにアクセスした画面。
![demo画面](https://dcj71ciaiav4i.cloudfront.net/D0B5A980-C9FC-11EB-ABD7-3362918AE194/images/intro/web.svg)

CATS ページと DOGS ページにリンクするようになっており、ALB により振り分けが行われる。

- CATS ページ：EC2 のコンテナにアクセス
- DOGS ページ：Fargate のコンテナにアクセス

## 最後に

前回、前々回のハンズオンよりもお膳立てされていた。  
**自分で操作せずに作成されたパーツが多すぎて逆に理解しにくいと感じた。**  
このハンズオン特有で学習できることも特になかったので、前回のハンズオンで十分だった。(復習にはなったのでよかった)  
まあまあ見た目の良い web サイトが準備されており、それを動作させることができるので最後に喜びはあると思う。
