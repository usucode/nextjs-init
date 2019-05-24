# Next.jsの環境構築

なぜNext.jsなのか
Gatsbyを利用すると色々便利なライブラリはあるが、そのおかげでライブラリの使い方をいちいち調べに行ったりで結構大変になる。
Next.jsは自分で構築していく感じがしてすごくわかりやすい。

例えるならGatsbyはRuby on RailsでNext.jsはExpressみたいな。
すごく必要最小限でわかりやすい。

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
1. インストール

```bash
yarn
# 自分でやる場合
yarn add react react-dom next
```

2. ビルド

```bash
yarn build
```

3. 通常起動

```bash
yarn start
```

4. 静的にビルド

```bash
yarn export
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