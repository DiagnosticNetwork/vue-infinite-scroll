# vue-infinite-scroll

vue-infinite-scroll is an infinite scroll directive for vue.js, forked to provide better W3C validity support, by using `data-` attributes to control options.

# Install

```Bash
npm install vue-infinite-scroll --save
```

### CommonJS

You can use any build tool which supports `commonjs`:

```JavaScript
// register globally
var infiniteScroll =  require('vue-infinite-scroll');
Vue.use(infiniteScroll)

// or for a single instance
var infiniteScroll = require('vue-infinite-scroll');
new Vue({
  directives: {infiniteScroll}
})

```

Or in ES2015:

```JavaScript
// register globally
import infiniteScroll from 'vue-infinite-scroll'
Vue.use(infiniteScroll)

// or for a single instance
import infiniteScroll from 'vue-infinite-scroll'
new Vue({
  directives: {infiniteScroll}
})

```

### Direct include

You can use the CDN: https://unpkg.com/vue-infinite-scroll, `infiniteScroll` is exposed to `window` and will automatically install itself. Also you can use your local copy:

```HTML
<script src="../node_modules/vue-infinite-scroll/vue-infinite-scroll.js"></script>
```

## Usage

Use v-infinite-scroll to enable the infinite scroll, and use infinite-scroll-* attributes to define its options.

The method appointed as the value of v-infinite-scroll will be executed when the bottom of the element reaches the bottom of the viewport.

```HTML
<div v-infinite-scroll="loadMore" data-infinite-scroll-disabled="busy" data-infinite-scroll-distance="10">
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

# data- Options

All attributes should be prefixed with `data-`, excluding `v-infinite-scroll`.

| Option | Description |
| ----- | ----- |
| data-infinite-scroll-disabled | infinite scroll will be disabled if the value of this attribute is true. |
| data-infinite-scroll-distance | Number(default = 0) - the minimum distance between the bottom of the element and the bottom of the viewport before the v-infinite-scroll method is executed. |
| data-infinite-scroll-immediate-check | Boolean(default = true) - indicates that the directive should check immediately after bind. Useful if it's possible that the content is not tall enough to fill up the scrollable container. |
| data-infinite-scroll-listen-for-event | infinite scroll will check again when the event is emitted in Vue instance. |
| data-infinite-scroll-throttle-delay | Number(default = 200) - interval(ms) between next time checking and this time  |

## Development

|Command|Description|
|---|---|
|npm run build|Build in umd format|
|npm test|Lint code|

# License

MIT
