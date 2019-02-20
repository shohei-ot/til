Map
=====

[Map \- JavaScript \| MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Map)

- `Object` と違い、 key には任意の値を設定できる。
- `Object` は `String`, `Symbol`のみ？
- `Map` は **任意の値** が key に使える。
    - 例えば `Object` もkeyに出来る。 (ただしその場合 `.get()` で指定する際は同一の参照である必要がある。)
    - 
      ```js
      const obj = {id: 1, name: "foo"}
      
      const map = new Map([
        [obj, "key is object"]
      ])
      
      map.get(obj) // => "key is object"
      map.get({id: 1, name: "foo"}) // => undefined
      ```
- keyの一致判定は`same-value` で処理される。
    - [等価性の比較と同一性 \- JavaScript \| MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Equality_comparisons_and_sameness#Same-value_equality)
    - > Same-value 等価性は Object.is メソッドによって提供されます。
    - 同一性の比較表なんてものがあった。 `Object.is` も載ってる。  
      https://developer.mozilla.org/ja/docs/Web/JavaScript/Equality_comparisons_and_sameness#A_model_for_understanding_equality_comparisons
