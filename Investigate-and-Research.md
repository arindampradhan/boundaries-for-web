# Investigate how Instagram PWA works

* How they implemented the image gallery in chrome ? Specially select image ?  
* Why is there scroll smooth and not ui blocking ?
* Why is their scroll view nicely loading ?
* Why does their individual image loading not performant ?
* Can some webassemby db be used for storing images like that of the native instagram app in the web?

# Experiment with webpack plugins & web assembly

* Try writing your own plugin for .wasm loaders
* question if they are meant to be used as .wasm or direct predecessor like .rs .py to import directly into javascript code
* **Rough idea:**

```js
    // by default(without plugins) will help wrap .wasm file extension
    new WasmPlugin({
        loaders: [
            {
                test: /\.(py|pyc)$/,
                loader: require.resolve('python-wasm-loader'),
                options: {
                    target: 'browser'
                }
            },
            {
                test: /\.(rs)$/,
                loader: require.resolve('rust-wasm-loader'),
                options: {
                    target: 'worker'
                }
            },
            {
                test: /\.(cpp)$/,
                loader: require.resolve('cpp-wasm-loader'),
                options: {
                    target: 'node'
                }
            },
        ]
    })
```
    

# Web Worker to create a division for UI thread (Main thread) and worker thread just like android

* How to fundamentally implement this ?
* An architecure to implement this system targeting mobile devices.


# understanding react-reconciler for better understanding react

* Tring to understand canvas and how reconciler can be used to target different environments.
* Same attempt was done by Flipboard in https://github.com/Flipboard/react-canvas when `react was in extreme hype :P`.
* [more examples](https://github.com/diegomura/react-pdf)
