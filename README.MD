# Overview
vue-infinite-scroll is an infinite scroll directive for vue.js.

# Install

```Bash
npm install vue-infinite-scroll --save
```

## Webpack

```JavaScript
require('vue-infinite-scroll');
```

## script tag

```HTML
<script src="../node_modules/vue-infinite-scroll/lib/index.js"></script>
```

# Usage

Use v-infinite-scroll to enable the infinite scroll, and use infinite-scroll-* attributes to define its options.

The method appointed as the value of v-infinite-scroll will be executed when the bottom of the element reaches the bottom of the viewport.

```HTML
<div v-infinite-scroll="loadMore()" infinite-scroll-disabled="busy" infinite-scroll-distance="10">
  ...
</div>
```

```JavaScript
var count = 0;

new Vue({
  el: '#app',
  data: {
    data: [],
    busy: false
  },
  methods: {
    loadMore: function() {
      this.busy = true;

      setTimeout(() => {
        for (var i = 0, j = 10; i < j; i++) {
          this.data.push({ name: count++ });
        }
        this.busy = false;
      }, 1000);
    }
  }
});
```

# Options

| Option | Description |
| ----- | ----- |
| infinite-scroll-disabled | infinite scroll will be disabled if the value of this attribute is true. |
| infinite-scroll-distance | Number(default = 0) - the minimum distance between the bottom of the element and the bottom of the viewport before the v-infinite-scroll method is executed. |
| infinite-scroll-immediate-check | Boolean(default = true) - indicates that the directive should check immediately after bind. Useful if it's possible that the content is not tall enough to fill up the scrollable container. |
| infinite-scroll-listen-for-event | infinite scroll will check again when the event is emitted in Vue instance. |

# License
MIT
