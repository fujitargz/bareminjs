# 関数

## 用語 {#words}
関数には名前（**関数名**）を付けることができます。
また、関数に渡す値を**引数**（arguments）といいます。
関数が返却する値は**戻り値**または**返り値**（return value）といいます。

## 関数の宣言方法 {#declaration}
宣言を宣言する方法は複数ありますが、最も基本的な方法は`function`キーワードを使う方法です。

`function`キーワードを用いて`function 関数名( 引数 ) { 処理 }`のように関数を宣言できます。

```js
function add(a, b){
  return a + b;
}
```

上の例では、`add`という名前の関数を宣言しています。関数`add`は引数を2つとり、その和を返します。
なお、関数の戻り値は`return`キーワードの後に記述します。

関数に引数を渡すと、関数を呼び出すことができます。

<!-- js-console -->
```js
function add(a, b){
  return a + b;
}

const sum = add(1, 2); // 関数addを呼び出す
console.log(sum);
```

上の例では、関数`add`に引数`1`、`2`を渡して実行し、その結果（戻り値）を変数`sum`で受け取り、表示しています。

ちなみに、関数に引数を渡さなければ、関数は呼び出されません。

<!-- js-console -->
```js
function add(a, b){
  return a + b;
}

const sum = add; // 引数を渡さない
console.log(sum);
```

上の例では、関数`add`に引数を渡していない（`add`の後に`()`がない）ため、関数`add`は呼び出されず、計算は行われていません。

## 関数と変数 {#funcandvar}

先の例では関数`add`を呼び出していませんでした。
したがって、変数`sum`には関数`add`の戻り値が代入されることはありません。

実は、先の例の場合、変数`sum`には関数`add`が代入されています。
したがって、変数`sum`を関数`add`だと思って引数を渡すと、関数`add`が呼び出されます。

<!-- js-console -->
```js
function add(a, b){
  return a + b;
}

const sum = add;
const result = sum(2, 3); // sumに引数を渡す
console.log(result);
```

このように、JavaScriptでは**関数を変数に代入可能**です。

## 無名関数 {#anonymous}

先の例で、変数`sum`に代入した関数`add`は、`sum`に引数を渡すことで呼び出せることを確認しました。
したがって、関数名`add`はもはや不要なので、省略可能です。

関数名の無い関数のことを**無名関数**または**匿名関数**といいます。
無名関数は、`function`の後に関数名を書かず、すぐに引数を書くことで宣言可能です。

<!-- js-console -->
```js
// 無名関数を宣言し変数sumに入れる
const sum = function(a, b){
  return a + b;
}

const result = sum(2, 3);
console.log(result);
```

## アロー関数 {#arrow}

`function`を使って無名関数を宣言しましたが、JavaScriptには無名関数をより簡潔に記述するための文法が定義されています。
それが**アロー関数**です。

アロー関数は`( 引数 ) => { 処理 }`のように記述します。
ただし、引数が1つの場合は`()`を省略可能です。
また、処理が`return`文のみの場合は`{}`と`return`を省略可能です。
即ち、以下の関数は全て同じ意味になります。

```js
// function
function(x){
  return x + 1;
}

// アロー関数
(x) => {
  return x + 1;
}

// 引数が1つなので()を省略
x => {
  return x + 1;
}

// 処理がreturnのみなので{}とreturnを省略
(x) => x + 1;

// ()の省略と{},returnの省略を組み合わせる
x => x + 1;
```

見慣れないかもしれませんが、`function`を使った場合に比べかなり簡潔な記述になりました。

慣れないうちは、アロー関数の名前の由来でもある`=>`の記号を探し、
その左に引数、右に処理、というようにコードを探しながら読むと良いでしょう。
また、`()`、`{}`、`return`が省略されたアロー関数は、
それらの記号を復元すると読みやすくなるかもしれません。

さて、先ほど`function`を用いて無名関数を以下のように宣言しましたね。

<!-- js-console -->
```js
// 無名関数を宣言し変数sumに入れる
const sum = function(a, b){
  return a + b;
}

const result = sum(2, 3);
console.log(result);
```

これをアロー関数で書き換えると以下のようになります。

<!-- js-console -->
```js
// 無名関数を宣言し変数sumに入れる
const sum = (a, b) => a + b;

const result = sum(2, 3);
console.log(result);
```

開発においても、上の例のように変数にアロー関数を代入することが多々あります。

特に、以下の例のように引数の`()`が省略されると通常の代入のように見えてしまうことがあるので、
アロー関数を一つのかたまりとして認識できるように目を慣らしておいてください。

<!-- js-console -->
```js
const increment = x => x + 1;

const num = increment(1);
console.log(num);
```