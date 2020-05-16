# Blockchain

## 仕組み（アルゴリズム）

ブロックチェーンとは、不変の連続したブロックと呼ばれる記録のチェーン。
取引の記憶をネットワークに参加している全員で共有することで、改竄される難易度を中央集権で記録を管理する場合よりも上げることを可能にしている。
改竄する場合は、書き換え時点から現在までの全てのハッシュを再計算して書き換える必要がある

### トランザクション

取引の記録で残さなければならない情報は次の３つ

- 宛先（誰に送るか）
- 差出人（誰が送ったか）
- 金額

これらの取引の内容をまとめて**トランザクション**と呼ぶ。
トランザクションに次の内容を加えて１セットの記録とする

- インデックス
- タイムスタンプ
- プルーフ
- 前のブロックのハッシュ

ハッシュは次の特徴を持っている

- 同じファイルから同じ値が得られる
- 少しでもファイルのデータが異なると全く異なる値になる
- ハッシュは簡単に生成できるが、ハッシュから元のファイルを復元するのはかなり大変

ブロックは、取引やファイル、あらゆるデータを格納することができ、ハッシュを使って繋がっている。

BlockChainクラスは、チェーンの扱いを司っている。
チェーンはトランザクションを格納し、新しいブロックをチェーンに加えるためのヘルパーメソッドを持っている。

全ての新しいブロックはそれまでの全てのブロックから生成されるハッシュを含んでいる

### 採掘

1. プルーフ・オブ・ワークを計算する
2. コインを採掘者に与えるトランザクションを加える
3. チェーンに新しいブロックを加えることで、新しいブロックを採掘する

### コンセンサスの問題

非中央集権であるが故に、同じチェーンを全員が反映していることを確認する必要がある。

## 実行環境

- macOS Mojave バージョン 10.14
- Python 3.8
  - Flask 1.1
  - requests 2.23.0

## 実行手順

### 1. 環境作成

プロジェクトファルダに移動し、venvを作成する。
```
$ python3 -m venv venv
```

### 2. 環境をアクティブに

```
$ . venv/bin/activate
```

### 3. インストール

```
$ pip install pipenv
```

```
$ pipenv install
```

### 4. サーバー起動

```
$ pipenv run python blockchain.py
```

## 参照：

* [ブロックチェーンを作ることで学ぶ 〜ブロックチェーンがどのように動いているのか学ぶ最速の方法は作ってみることだ〜 - Qiita](https://qiita.com/hidehiro98/items/841ece65d896aeaa8a2a)

* [Learn Blockchains by Building One | Hacker Noon](https://hackernoon.com/learn-blockchains-by-building-one-117428612f46)

* [dvf/blockchain: A simple Blockchain in Python](https://github.com/dvf/blockchain/blob/master/blockchain.py)

* [Mastering Bitcoin](https://bitcoinbook.info/wp-content/translations/ja/book.pdf)

* [インストール— Flaskドキュメント（1.1.x）](https://flask.palletsprojects.com/en/1.1.x/installation/)
