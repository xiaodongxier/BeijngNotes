
# vue-props传值

![vue-props传值](https://gitcdn.xiaodongxier.com/image/note-page/20230809133912.png)

```html
<template>
  <div class="todo">
    <h2>todo</h2>
    <ol>
      <todo-item v-for="item in itemList" :key="item.id" :propsString="item.title" :propsArray="propsArray"></todo-item>
    </ol>
  </div>
</template>

<script>
import TodoItem from './demo/demo1-todoitem.vue'
export default {
  name: 'HelloWorld',
  data () {
    return {
      itemList: [
        {
          id: '0',
          // title: '事件1'
        }
      ],
      propsArray: []
    }
  },
  components: {
    TodoItem
  }
}
</script>
<style scoped>
</style>
```


```html
<template>
  <div>
    <li> {{ propsString }} </li>
    <div>{{ propsArray }}</div>
  </div>
</template>

<script>
export default {
props: {
  propsString: {
    type: String,
    // 默认值，没有值的时候显示
    default: '空字符串'
  },
  propsArray: {
    type: Array,
    // 默认值，没有值的时候显示
    default: () => {
      return "空数组"
    }
  }
}
}
</script>

<style>

</style>
```