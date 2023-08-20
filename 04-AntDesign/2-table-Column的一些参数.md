# table-Column的一些参数


## Table

- expandedRowKeys
  - 说明： 展开的行，控制属性。可用 .sync 后缀, 参见 update:expandedRowKeys
  - 类型：string[]

- rowSelection
  - 说明： 列表项是否可选择，[配置项](https://1x.antdv.com/components/table-cn/#rowSelection)
    - ![配置项](https://gitcdn.xiaodongxier.com/image/note-page/20230810163256.png)
  - 类型：	object
  - 默认值： null

- rowKey`
  - 说明：表格行 key 的取值，可以是字符串或一个函数
  - 类似：string|Function(record):string
  - 默认值： 'key'

## Column


- customRender
  - 说明： 生成复杂数据的渲染函数，参数分别为**当前行的值**，**当前行数据**，**行索引**，@return 里面可以设置表格行/列合并,可参考 demo 表格行/列合并
  - 类型： Function(text, record, index) {}|slot-scope

```js
const columns = [
  {
    title: "核电厂名称",
    dataIndex: "name",
    key: "name"
  }, {
    title: "装机容量(万千瓦)",
    dataIndex: "capacity",
    key: "capacity",
    // (行的值，行数据，行索引)
    // 可以根据后端返回的数字来进行判断具体显示的值(1 or 2 or 3)
    // 比如1位电厂 ，2为反应堆，3为其他
    customRender: function(text) {
      if (text === 0) {
        return "电厂";
      } else if (text === 1) {
        return "反应堆";
      } else if (text === 2) {
        return "其他";
      } else {
        return text;
      }
    }
  }
];
```



- scopedSlots
  - 说明： 使用 columns 时，可以通过该属性配置支持 slot-scope 的属性，如 scopedSlots: { customRender: 'XXX'}
  - 类型： object
