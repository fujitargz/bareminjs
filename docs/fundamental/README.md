# 準備

## 値の表示 {#log}

JavaScriptでは、`console.log()`を用いて値を表示することができます。

<!-- js-console -->
```js
console.log('表示される文字列');
```

## コメント {#comment}

JavaScriptでは、**コメント**は実行されません。

ソースコードのうち、`/* */`で囲んだ部分はコメントとして扱われます。

<!-- js-console -->
```js
/* console.log(1); */
console.log(2); /* console.log(3); */ console.log(4);
```

また、`//`から行末までの部分もコメントとして扱われます。

<!-- js-console -->
```js
// console.log('a');
console.log('b'); // console.log('c'); console.log('d');
```

既存のコードの一部をコメントにして無効化することを、**コメントアウトする**ということがあります。

例えば、次のコードにおいて

```js
console.log('foo');
console.log('bar');
```

1行目をコメントアウトすると、次のようなコードになります。

```js
// console.log('foo');
console.log('bar');
```