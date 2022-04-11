# ESModule

## 浏览器加载

### 使用`<script>`标签加载外部脚本

```javascript
<script type='module' src='./index.js'></script>
```

浏览器对于带有`type="module"`的`<script>`，都是异步加载，不会造成堵塞浏览器，等同打开了`<script>`标签的`defer`属性。

```javascript
<script type='module' src='./index.js' defer></script>
```

### 也允许内嵌在网页中，语法行为与加载外部脚本完全一致

```javascript
<script type='module'>import A from './index.js'</script>
```

### Import Maps

```html
<script type="importmap">
  {
    "imports": {
      "vue": "https://unpkg.com/vue@3/dist/vue.esm-browser.js",
      "utils": "./utils.mjs"
    }
  }
</script>
<script type="module">
  import vue from 'vue';
  import utils from 'utils';
  // TODO something
</script>
```
