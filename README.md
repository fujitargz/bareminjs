# [bareminjs](https://kazuhiro-f.github.io/bareminjs/)

## Getting Started

`yarn`のみ利用可能

```
yarn install
```

## Available Scripts

ローカル確認用

```
yarn serve
```

[localhost:4000](http://localhost:4000)でアクセス可能

## Notes

* 開発時は適宜`develop`ブランチから feature ブランチを切ってください。
* feature ブランチは`develop`ブランチにマージしてください。
* `main`はリリース用ブランチです。
* `main`に push があると自動で`gh-pages`ブランチにデプロイされます。
* [`HonKit`](https://github.com/honkit/honkit)を使用しています。書き方は[`HonKit`のドキュメント](https://honkit.netlify.app/)を参考にしてください。
* 以下の plubin を利用しています。
  * [gitbook-plugin-js-console](https://github.com/azu/codemirror-console/tree/master/packages/gitbook-plugin-js-console)