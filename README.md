# 開発議事録

## 開発テーマ
### 料理
- ユーザーが料理名を入れたらその調理方法がかえってくるwebアプリ
- できればマイページを作りユーザーが保存した料理を見れるようにしたい。(DBを使う?)

## プロジェクトの機能要件
### 1. APIエンドポイントの作成
#### エンドポイントの詳細
- [ ] 選択したテーマに関連するデータを提供するためのエンドポイントを設計してください。これにはリスト表示、詳細表示、検索機能、データの集計などが含まれます。
- [ ] エンドポイントがデータのフィルタリング、ソート、ページ分けをサポートするようにしてください。

#### テーマに適したデータを生成してください。以下の方法から選択してください。(2つのうち一つ選択)
- [ ] テーマに合ったデータを返す無料のWeb APIをバックエンドから呼び出す。
- [ ] ランダムなデータを生成する独自のプロセスや、可能な文字列を列挙する設定ファイルを利用する。
      
#### データの形式
- [ ] 様々なタイプのデータのためにGoの構造体を作成します。
- [ ] すべてのWebエンドポイントは、結果をJSON形式で含むHTTPレスポンスを返すようにしてください。

### 2. APIドキュメンテーションの作成
- [ ] 利用可能なエンドポイント、リクエストとレスポンスの形式、使用例について詳細に説明したAPIの包括的なドキュメントを作成してください。このドキュメントは、専用のウェブサイトからアクセスできるようにし、開発者がAPIを容易に利用できるように必要な情報を提供してください。

### 3. デモWebアプリケーションの開発
- [ ] APIからデータを取得して表示するシンプルなWebアプリケーションを開発してください。このアプリケーションはAPIの主要な機能を示し、潜在的な開発者に対する参考例となるように設計してください。


## 想定されるwebAPI
### Edamam
下のURLはEdamamが提供しているレシピ検索用のwebAPIドキュメントで、このAPIを使用することでEdamamのデータベースからレシピを検索し、取得することができる。以下要約。

1. エンドポイント
- https://api.edamam.com/search というエンドポイントを使っている。
- クエリパラメータを使って検索要件を指定できる。
2. 検索要件
- 検索クエリにはキーワード、カテゴリ、栄養素がある。
- JSONをみると複雑だが、料理の難易度や料理の種類も指定できる。
3. レスポンス
- APIはJSON形式
- レスポンスにはレシピタイトル、説明、材料等が含まれる。
4. 認証
- APIキーを使用している。

### webAPI
https://developer.edamam.com/edamam-docs-recipe-api
### リクエスト
https://api.edamam.com/doc/open-api/recipe-search-v2.json



## 大まかな開発手順

- [ ] 個人でgoで小さいwebAPIデモアプリケーションを作る。
- [ ] フロント側をHTML/CSS&JavaScriptで作る。
- [ ] webAPIが返すJSONの内容を決める。
- [ ] エンドポイントの設計を本格的に開発する。
- [ ] 決めた内容を開発する。
- [ ] 時間があれば本番環境を整えNGINXでデプロイする。



## 2/24の開発議事録
1. 開発テーマを決めた。メンバーに料理好きがいるとのことだったので大体の構想はクックパッドを想定している。
2. 想定されるAPIについて決めた。
3. webAPIの開発のためにドキュメントにある簡単な課題を開発していく
4. 大まかな開発手順


### 課題の要件
開発に着手する前に、ドキュメントにあるコードを拡張してみる。2/25に以下の要件を加えて提出。
- [x] /api/categories：カテゴリの配列を含むJSONを返します。これらのカテゴリにはlorem ipsumを使用するか、ランダムに文字列を生成するか、あるいは固定の設定ファイルを使用することができます。

- [x] /api/calculator?o={operator}&x={x}&{y}：指定された2つのオペランド（xとy）に対して、指定された演算子（o）を使って計算を行い、その結果を返します。サポートされる演算子には、加算（+）、減算（-）、乗算（*）、除算（/）があります。

## 2/25の開発議事録
1. 自分たちで要件1を満たす簡単なgoのデモアプリケーションを作成する
2. JSON形式でDBのような基本機能を備えておく必要がアリ

### デモアプリケーションの要件
- [ ] [プロジェクトの機能要件](#プロジェクトの機能要件) の1に従う簡単プロトタイプアプリケーションを開発する

## 2/28の開発議事録
1. アクティビティ図作成。
2. 検索についてフロントまで含めた開発を進めていく。

### バックエンド側のアクティビティ図
#### エンドポイントの設計
```mermaid
graph LR;
    A[クライアント:ユーザーがカレーを入力] -- リクエスト --> B[サーバー:JSONファイルからカレーIDを取得];
    B -- JSONレスポンス: クライアントにカレーの詳細データを表示 --> A;
```


 ## 3/2の開発議事録
 1. Edamamを使ったwebAPIの表示(カレーとユーザーが送ったらレスポンスがかえってくる)
 2. フロント側の処理の追加

### 追加・削除・更新について
おそらくデータベースを用いないと開発できない。

### 完成したもののイメージ例(フロント)
https://kanatanagano.github.io/Library-Application/

### 明日13:00からoviceでedamamを活用していきます

## 3.3の開発議事録
1. htmlとgoとの連携を可能にさせた
2. ginをつかって高速化は面白そう

### 他チームとの差別化
a,bチームがDBを使っているのでこちらはフレームワークを使ってみよう

