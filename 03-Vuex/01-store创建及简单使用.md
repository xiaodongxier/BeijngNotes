# Vuex

![Vuex](https://gitcdn.xiaodongxier.com/image/note-page/20230807063134.png)


## 使用步骤

1. 创建 store 仓库

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

2. 全局引入

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


3. 组件中获取 vuex 状态 






- 组件中获取vuex中store仓库中的数据

```js
this.$store.state.test
```

