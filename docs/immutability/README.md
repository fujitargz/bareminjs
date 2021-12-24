# 発展：immutability

<ruby><rb>immutability</rb><rp>（</rp><rt>イミュータビリティー</rt><rp>）</rp></ruby>（不変性）は、関数型プログラミング由来の概念です。

簡単にいうと、
* 値（変数の中身）は書き換えないようにしましょう
* 値（変数の中身）を変更したいなら新しい値（変数）をつくりましょう
* そうすればプログラムの品質が上がりますよ

という考え方です。

例えば、氏名を表すオブジェクト`{ firstName: '名前', lastName: '苗字' }`の配列から苗字だけを取り出して配列を作成するプログラムを考えてみましょう。
次のプログラムは値を書き換えない（immutableな）方法で実装しています。

<!-- js-console -->
```js
// immutable
const names = [
  {
    firstName: '一郎',
    lastName: '鈴木'
  },
  {
    firstName: '次郎',
    lastName: '佐藤'
  },
  {
    firstName: '花子',
    lastName: '山田'
  },
  {
    firstName: '三郎',
    lastName: '田中'
  }
];

// namesは書き換えずに
// 新しい配列firstNamesを作っている
const lastNames = names.map(e => e.lastName);

console.log('苗字: ' + lastNames);
```

次に、同じプログラムを値を書き換える（mutableな）方法で実装してみます。

<!-- js-console -->
```js
// mutable
let names = [
  {
    firstName: '一郎',
    lastName: '鈴木'
  },
  {
    firstName: '次郎',
    lastName: '佐藤'
  },
  {
    firstName: '花子',
    lastName: '山田'
  },
  {
    firstName: '三郎',
    lastName: '田中'
  }
];

// namesの内容を書き換え
names.forEach((elem, ind, arr) => arr[ind] = elem.lastName);

console.log('苗字: ' + names);
```

ここまでは大差ありませんね。

では次に、苗字ではなく名前を取り出してみましょう。

immutableな実装は次のようになります。

<!-- js-console -->
```js
// immutable
const names = [
  {
    firstName: '一郎',
    lastName: '鈴木'
  },
  {
    firstName: '次郎',
    lastName: '佐藤'
  },
  {
    firstName: '花子',
    lastName: '山田'
  },
  {
    firstName: '三郎',
    lastName: '田中'
  }
];

const lastNames = names.map(e => e.lastName);

console.log('苗字: ' + lastNames);

// ここから追記
// immutableな実装をしていたのでnamesはそのまま保存されているので
// 名前を取り出す処理を追加すればよい
const firstNames = names.map(e => e.firstName);

console.log('名前: ' + firstNames);
```

簡単に追加できました。

では、mutableな実装ではどうでしょうか。

<!-- js-console -->
```js
// mutable
let names = [
  {
    firstName: '一郎',
    lastName: '鈴木'
  },
  {
    firstName: '次郎',
    lastName: '佐藤'
  },
  {
    firstName: '花子',
    lastName: '山田'
  },
  {
    firstName: '三郎',
    lastName: '田中'
  }
];

names.forEach((elem, ind, arr) => arr[ind] = elem.lastName);

console.log('苗字: ' + names);

// ここから追記
// namesは苗字の配列に書き換えられているので、
// 単純に処理を追加しようとすると...

names.forEach((elem, ind, arr) => arr[ind] = elem.firstName);

console.log('名前: ' + names);
```

はい、mutableに実装していたので、苗字を取り出した時点で名前が消えてしまっていました。
では、苗字を取り出す前に名前を取り出せば良いのでしょうか？

<!-- js-console -->
```js
// mutable
let names = [
  {
    firstName: '一郎',
    lastName: '鈴木'
  },
  {
    firstName: '次郎',
    lastName: '佐藤'
  },
  {
    firstName: '花子',
    lastName: '山田'
  },
  {
    firstName: '三郎',
    lastName: '田中'
  }
];

// 苗字の取得前に名前を取得すると...
names.forEach((elem, ind, arr) => arr[ind] = elem.firstName);

console.log('名前: ' + names);

names.forEach((elem, ind, arr) => arr[ind] = elem.lastName);

console.log('苗字: ' + names);
```

今度は名前を取り出した時点で苗字が消えてしまいました。

このように、mutableな実装では、**変数が宣言された後どこかで書き換えられる可能性**を考慮する必要があります。
また、値を書き換えると、**書き換え前の値が利用できなくなってしまいます**。

一方、immutableな実装では変数が書き換えられることがないため、**安全性**が高まります。
また、値を次々とコピーして（新しい値にして）いくため、**値の再利用が容易**です。

ちなみに、配列のプロトタイプメソッドのうち、本書で紹介した`map`、`filter`は新しい配列を返すため、mutableな実装に最適です。
このようなメソッドを**非破壊的メソッド**といいます（もとの配列を書き換えて破壊してしまうことがないため）。

一方、`forEach`、`sort`などのメソッドはもとの配列を書き換えるため、mutableな実装になってしまいます。
このようなメソッドは**破壊的メソッド**と呼ばれます。

プロトタイプメソッドを調べる時は、破壊的なのか非破壊的なのかも確認するようにしましょう。