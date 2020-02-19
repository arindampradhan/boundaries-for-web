# Guidelines to writing code for mobile devices | Android

## Rendering performance

* [Minimizing browser reflow](https://developers.google.com/speed/docs/insights/browser-reflow?hl=en)
* Use a class-centric methodology like BEM.  .blockname__element--modifier
* Reduce the complexity of your selectors. Reduce the number of elements being styled.
* Avoid style changes in input handlers 
* Reduce html depth
* Debounce your scroll handlers
* [List of events and css classes to avoid reflows](https://gist.github.com/paulirish/5d52fb081b3570c81e3a)

## Loading performance

* disable the browser cache to ensure you get accurate statistics for first-load performance
* [Follow PRPL pattern if possible](https://developers.google.com/web/fundamentals/performance/prpl-pattern/) i.e:
    * react-router + dynamic-import(code-splitting) + service-worker +  `<link rel="preload">` +  HTTP/2 Push.
    * pure js + service-worker + `<link rel="preload">` + `<script async>` +  HTTP/2 Push
* Debounce input handlers
* Avoid micro-optimizing your JavaScript
* Learn to use **(memory & performance tab)** of chrome dev tools - you can profile javascript and see execution time of the longest running function - you can search in performance > bottom-up (in the bottom panel) > sourcemap(if installed) of the file
* you can get the size of the heap and function execution from this two tab.
* Avoid using large js objects in general

## React/es(6-7) based stack and measures to take 

* Please use React.memo or purecomponent to avoid extra re-renders and reflows. (Availale above 16.7)
* Please use stable keys in React in for loops, don't use index. (It effects a lot of re-renders and performance)
* Please use pollyfill service to support older browsers (for backward compatibility) while using es6 features like  promise, Array.isarray, etc.:
    * Automatic solution  3rd party - (Pollyfill.io)[https://polyfill.io/v3/]... just add `<script src="https://polyfill.io/v3/polyfill.min.js">`
    * Manual (install core-js in es6 projects)[https://github.com/zloirock/core-js]
    * React will transpile down to es5 but not every es6 feature... so use thoughtfully what es6 features are being used


# About Mobile webview

* Android device below 4.3 uses webkit-534
* Android device from 4.4 uses chromium (supports most of the es6 features)

