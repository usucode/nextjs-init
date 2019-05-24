なぜNext.jsなのか
Gatsbyを利用すると色々便利なライブラリはあるが、そのおかげでライブラリの使い方をいちいち調べに行ったりで結構大変になる。(自分だけかも)
Next.jsは自分で構築していく感じがすごく必要最小限でわかりやすい。

また公式の勉強できる環境が揃っているのでぜひ使ってください。
参考: https://nextjs.org/learn/

## 環境

```
.
├── README.md
├── next.config.js # 静的ビルドの設定ファイル
├── node_modules
├── out # 静的なアウトプット
├── package.json
├── pages # ソースコード
└── yarn.lock
```

`package.json`は以下です。  
環境に合わせて変更して使ってください

```json
{
  "dependencies": {
    "next": "^8.1.0",
    "react": "^16.8.6",
    "react-dom": "^16.8.6"
  },
  "scripts": {
    "dev": "next",
    "build": "next build",
    "start": "next start",
    "export": "next export"
  },
  "devDependencies": {}
}
```

## How to use
### 1. インストール

```bash
yarn
# 自分でやる場合
yarn add react react-dom next
```

### 2. ビルド

```bash
yarn build
```

### 3. 静的にビルド

```bash
yarn export
```

`export`に成功するとルートディレクトリに`out`というディレクトリが生成されます。
これが静的なサイトです。

```
yarn global add serve
cd out
serve -p 8080
```
ブラウザで`http://localhost:8080/`で確認できます。
![スクリーンショット 2019-05-24 15.21.58.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/415529/5634f8f2-f4dd-25be-ec46-74036a153e57.png)


### 通常起動
通常に起動する場合なので、静的サイトにビルドしたい場合はいらない。

```bash
yarn start
```



## 静的サイトのビルドに必要なもの

ルートディレクトリに`next.config.js`を追加する必要がある。
サンプルの書き方を書いておきます。

```js
module.exports = {
  exportPathMap: function () {
    return {
      '/': {
        page: '/'
      },
      '/second': {
        page: '/second'
      }
    }
  }
}
```

ここから接続されるURLと表示するテンプレートを選択する。
また、ここで値を入れることもできるのでDBから取り出した値をここに入れることができそう。
