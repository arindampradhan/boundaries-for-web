Webworkers in Redux
===================

The target of those restrictions is to çreate opiniated rules to create a near native speed in low spec android devices.

To understand the topic [watch this video | main thread overworked](https://www.youtube.com/watch?v=7Rrv9qFMWNM)

The target is to port the redux stores in web workers and only make react use the main thread.

## About webworkers

* [Things that work: Functions available ](https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Functions_and_classes_available_to_workers)
* `localStorage`, `sessionStorage`, `history` not available. So midddlerwares like `connected-react-router` and `redux-presist` will have issues.
* Project found: 
    * [redux-worker-middleware](https://github.com/keyz/redux-worker-middleware) not complete solution, only migrates reducers to workers.
    * [redux-in-worker](https://github.com/dai-shi/redux-in-worker) is performant but will have issues with middleware using history api or localstorage.
* Workaround: Use `comlink` & `worker-plugin` manually where needed or wrap both to make it easier to use.
* [Eslint configuration to target worker](https://eslint.org/docs/4.0.0/user-guide/configuring#specifying-environments) add those to worker files while writing code so that you will get errors while using window api methods.

* **to be continued...**
