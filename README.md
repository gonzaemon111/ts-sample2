# TS サンプル

[参考サイト](https://qiita.com/notakaos/items/3bbd2293e2ff286d9f49)

### 開発の効率をあげる (ts-node & ts-node-dev)

tsc コマンドでコンパイルして node でプログラムが実行できるようになりました。
しかし、ソースコードを修正するたびに tsc を実行し、さらにそのあと node コマンドを実行するのは手間がかかりますね。
開発効率をあげるため、 tsc -> node の実行を自動的に行ってくれる ts-node パッケージを追加します。


`~/typescript-node-base`
```shell
$ npm install -D ts-node
```
パッケージが追加されたら ts-node コマンドを実行してみましょう。

`~/typescript-node-base`
```shell
$ npx ts-node src/index.ts
```
`実行結果`
`Hello, World!`

通常の node コマンドで JavaScript を実行するかのように、ts-node で TypeScript ファイルが実行できました。

ts-node で少し効率があがりました。ただ、ソースコードを修正するたび、毎回手動で実行する必要があります。

さらに開発効率をあげるため、ソースコードの変更を検知するたびに自動的に再実行してくれる ts-node-dev パッケージを追加します。

```shell
$ npm install -D ts-node-dev
```

パッケージが追加されたら ts-node-dev コマンドを実行してみましょう。

注: APIサーバーのように一度実行すると動き続けるプログラムではなく、この記事のHello Worldプログラムのように1度実行するとプロセスが終了するプログラムの場合は、ts-node-dev に --respawn オプションをつけます。

### rimraf npm-run-all パッケージの追加と npm-scripts に clean / tsc / build / start を追加

```shell
$ npm install -D rimraf npm-run-all
```

```shell
// TypeScript -> JavaScript に変換
npm run build

// 生成されたJavaScriptを実行
npm run start
// または
npm start

// 生成されたファイルを削除
npm run clean
```