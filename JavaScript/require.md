require
=========

## `require()` とは

CommonJS 形式で他のJSファイルを読み込む際の方法。  
学生の時、 Titanium Mobile 触っていた頃に初めて出会った。  
ES modules とは違ってその場所にコードを全て持ってくる。(Webpack 等で Tree Shaking されない)

Webpack の `require.context` は Webpack 独自の拡張。  

## 使い方

```js
const _ = require("lodash")
_.forEach(...)
```

みたいな。  
個人的には ES Modules の方が好き。Tree Shaking 効くし。

## 備考

### TypeScript

TS で JS を `require` で読み込むと、型定義が無くても警告されず、 `any` として扱ってくれる。  
苦肉の策として有効。  

