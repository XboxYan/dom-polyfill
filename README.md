# dom-polyfill

polyfill for DOM API

### 1.replaceChildren

```js
(function (item) {
    if (item.hasOwnProperty('replaceChildren')) {
        return;
    }
    Object.defineProperty(item, 'replaceChildren', {
        configurable: true,
        enumerable: true,
        writable: true,
        value: function append() {
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
    });
})(HTMLElement.prototype);
```

https://developer.mozilla.org/en-US/docs/Web/API/ParentNode/replaceChildren

[demo](demo/replaceChildren.html)
