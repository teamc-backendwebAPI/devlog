# 開発議事録

## 開発テーマ
### 料理
- ユーザーが料理名を入れたらその調理方法がかえってくるwebアプリ

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

- [ ] goで小さいwebAPIデモアプリケーションを作る。
- [ ] フロント側をHTML/CSS&JavaScriptで作る。
- [ ] webAPIが返すJSONの内容を決める。
- [ ] 決めた内容を開発する。
- [ ] 時間があれば本番環境を整えNGINXでデプロイする。



## 2/24日の開発議事録
1. 開発テーマを決めた。メンバーに料理好きがいるとのことだったので大体の構想はクックパッドを想定している。
2. 想定されるAPIについて決めた。
3. webAPIの開発のためにドキュメントにある簡単な課題を開発していく
4. 大まかな開発手順


### 課題の要件
開発に着手する前に、ドキュメントにあるコードを拡張してみる。2/25に以下の要件を加えて提出。
- [ ] /api/categories：カテゴリの配列を含むJSONを返します。これらのカテゴリにはlorem ipsumを使用するか、ランダムに文字列を生成するか、あるいは固定の設定ファイルを使用することができます。

- [ ] /api/calculator?o={operator}&x={x}&{y}：指定された2つのオペランド（xとy）に対して、指定された演算子（o）を使って計算を行い、その結果を返します。サポートされる演算子には、加算（+）、減算（-）、乗算（*）、除算（/）があります。
