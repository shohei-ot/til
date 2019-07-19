Worker
============

## Web Worker (Dedicated Worker)

JSでマルチスレッド。

### 使い方

```js
// メインスレッド
const worker = new Worker('path/to/worker.js')
worker.onmessage = e => {
    console.log(e.data) // => 10
}
const foo = 5
worker.postMessage(foobar)
```

```js
// worker.js
addEventListener('message', e => {
    postMessage(e.data * 2)
})
```

#### with Webpack (worker-loader)

```js
// webpack config
module.exports = {
    module: [
        {
            test: /worker\.js/,
            loader: 'worker-loader'
        }
    ]
}
```

```js
// app.js
import MyWorker from 'path/to/my.worker.js'

const worker = new MyWorker() // ← DOM の Worker の引数と異なる。
worker.onmessage = /* ... */
worker.postMessage(/* ... */)
```

loaderを設定しなくても import 時にインラインで噛ませられる。

#### in Jest (without worker-loader)

```shell
npm install -D jsdom-worker
```

```json
{
    "jest": {
        "setupFile": [
            "jsdom-worker"
        ]
    }
}
```

#### in Jest (with worekr-loader)

- `worker-loader` と取り回し方が違ってくるので、 `worker-loader` を使う場合は Jest で WebWorker を動かすことは諦める必要があるかも。
- 諦めて、Worker の呼び出しを行う部分をモックしてあげる。


WIP