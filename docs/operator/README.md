# 演算子 [WIP]

* 式
  * 評価
* 演算子
  * オペランド
  * 単項演算子
    * `typeof`
    * `!`
      * `!!`で`boolean`化
  * 二項演算子
    * 算術演算子
      * `+`
        * `number`なら加算、`string`なら結合
      * `-`
      * `*`
      * `/`
      * `%`
    * 比較演算子
      * `<`
      * `>`
      * `<=`
      * `>=`
        * `=>`は全く別の意味
        * greater than or equal toか、arrowか
    * 等価演算子
      * `===`
      * `!==`
    * 論理演算子
      * `&&`
      * `||`
      * 論理値を扱う限り`AND`、`OR`
  * 三項演算子
    `? :`
* 演算の優先順位
  * `()`内が優先