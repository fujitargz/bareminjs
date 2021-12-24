# プロトタイプメソッド

JavaScriptの配列には、予め定義されているメソッドやプロパティが存在します。
それらのことを**プロトタイプメソッド**や**プロトタイププロパティ**と呼びます。

プロトタイプメソッドやプロトタイププロパティは全ての配列に必ず定義されているので、
`配列.プロトタイプメソッド(引数)`のように呼び出すことができます。

## 配列のプロトタイププロパティ {#arrayprop}

### `Array.prototype.length`

配列には`length`というプロトタイププロパティが存在します。
`length`は文字通り配列の要素数（長さ）を表します。

<!-- js-console -->
```js
const ar = ['first', 'second', 'third'];
const len = ar.length; // 配列のlengthを取得
console.log(len);
```

## 配列のプロトタイプメソッド {#arraymethod}

### `Array.prototype.map`

`map`は、引数に関数（コールバック関数と呼ばれます）を受け取ります。
そして、受け取った関数を配列の各要素に順番に適用し、返り値を集めて新たな配列を作成し、その配列を`map`の返り値として返します。
即ち、配列中の全ての値をコールバック関数で新たな配列にマッピングし、その配列を返すメソッドです。

なお、コールバック関数を写像、配列を集合と考えると、像を返すメソッドと考えることもできます。

#### コールバック関数のシグネチャ
`map`が配列のそれぞれの要素にコールバック関数を適用するとき、与えられる引数は以下のように決められています。
* 第一引数は要素そのもの（の値）
* 第二引数は要素の添え字
* 第三引数は配列そのもの

<!-- js-console -->
```js
// mapに渡すコールバック関数
const callback = (element, index, array) => {
  const val = 'element: ' + element;
  const ind = 'index: ' + index;
  const ar = 'array: ' + array;
  return val + ' ' + ind + ' ' + ar;
}

const ar = ['1st', '2nd', '3rd'];

// mapにコールバック関数を渡して呼び出し
const res = ar.map(callback);

console.log(res);
```

実際の開発では、第三引数まで利用することは少ないです。

<!-- js-console -->
```js
// 値の2倍を返す関数
// 第一引数のみ利用する
const double = e => e * 2;

const array = [1, 2, 3];

const doubled = array.map(double);

console.log(doubled);
```

また、上の例ではコールバック関数を予め宣言しましたが、多くの場合コールバック関数は使い捨てなので、
都度宣言するよりも`map`の中でアロー関数を用いて書いてしまうことが多いです。

<!-- js-console -->
```js
const array = [1, 2, 3];

const doubled = array.map(e => e * 2);

console.log(doubled);
```

### `Array.prototype.filter`

`filter`も引数に関数（コールバック関数）を受け取ります。
そして、配列の各要素にコールバック関数を適用し、返り値が`true`になる要素のみを集めて新たな配列を作成し、その配列を返します。
即ち、コールバック関数を用いて配列をフィルタリングするメソッドです。

`filter`のコールバック関数も、第一引数に要素そのもの（の値）、第二引数に要素の添え字、第三引数に配列そのものを受け取ります。

<!-- js-console -->
```js
// 値が20以上ならばtrue、そうでなければfalseを返す関数
const isAdult = age => age >= 20;

const people = [18, 22, 20, 14, 30];

const adults = people.filter(isAdult);

console.log(adults);
```