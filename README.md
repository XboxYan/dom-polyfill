# dom-polyfill

polyfill for DOM API

### 1.replaceChildren

```js
/**
* replaceChildren.js
* @mdn https://developer.mozilla.org/en-US/docs/Web/API/ParentNode/replaceChildren
* @email yanwenbin1991@live.com
**/
(function (item) {
    if (!item.replaceChildren) {
        item.replaceChildren = function () {
            var parentNode = this;
            var oldNodes = [].slice.call(parentNode.childNodes);
            var newNodes = [].slice.call(arguments);
            oldNodes.forEach(function (nodes) {
                if (!newNodes.find(function(el){ return el === nodes})) {
                    parentNode.removeChild(nodes)
                }
            });
            parentNode.append.apply(this,newNodes);
        }
    }
})(HTMLElement.prototype);
```

https://developer.mozilla.org/en-US/docs/Web/API/ParentNode/replaceChildren

[demo](https://xboxyan.codelabo.cn/dom-polyfill/demo/replaceChildren.html)
