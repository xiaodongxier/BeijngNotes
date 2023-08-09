# Vuex

![Vuex](https://gitcdn.xiaodongxier.com/image/note-page/20230808064728.png)


## State

### 1. 创建 store 仓库

> src/store/index.js

```js
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex)

const store = new Vuex.Store({
  state: {
    test: 'store值-test'
  },
  mutations: {
    setTest(state){
      
    }
  }
})
export default store
```

### 2. 全局引入

> src/main.js

```js
import Vue from 'vue'
import App from './App'
import router from './router'
import store from './store' // 引入 store

Vue.config.productionTip = false

new Vue({
  el: '#app',
  store,   // 挂载 store
  router,
  components: { App },
  template: '<App/>'
})
```


### 3. 组件中获取 vuex 状态 

<!-- #### 3.1 组件中获取vuex中store仓库中的数据 -->

1. this.$store.state.test

```js
this.$store.state.test
```

2. mapState (扩展运算符的方式)

Store内容

```js
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex)

const store = new Vuex.Store({
  state: {
    test: '｜===store值-test===｜',
    maptest1: "====mapState数据===="
  },
  mutations: {
    setTest(state){
      
    }
  }
})
export default store
```

组件获取vuex内容
```js
import { mapState } from 'vuex';
export default {
  name: 'HelloWorld',
  computed: {
    // 字符串形式进行读取
    ...mapState(['maptest1'])
  }
}
```


## Mutation

> 更改 Vuex 的 store 中的状态的唯一方法是提交 mutation。

