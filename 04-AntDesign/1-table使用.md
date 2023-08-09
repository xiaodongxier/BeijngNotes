# table的使用


`columns1` 为表头，`data1` 为数据源

其中`columns1` 中的 `dataIndex` 的值与 `data1` 中的值一一对应

---

- a-table 
  - :columns="columns"  - 表头
  - :data-source="data1"  - 数据源
  - bordered - 添加边框
  - :row-selection="rowSelection" - 选中/取消操作

- columns
  - ellipsis: true  - 超出省略号



```html
<template>
  <div>
    <a-table 
    :columns="columns" 
    :data-source="data" 
    bordered
    :row-selection="rowSelection"
    :indentSize=10
    >
    </a-table>
  </div>
</template>
<script>
const columns = [
  {
    dataIndex: "name",
    title: "电厂名称",
    // 宽度不变，超出内容省略
    ellipsis: true,
  },
  {
    dataIndex: "type",
    title: "类型"
  },
  {
    dataIndex: "time",
    title: "时间"
  },
  {
    dataIndex: "edit",
    title: "操作"
  }
];

const data = [
  {
    name: "秦山电厂",
    key: "秦山电厂",
    type: '电厂',
    time: 2023,
    children: [
      {
        name: "第二反应堆",
        key: "第二反应堆",
        type: "反应堆",
        time: 2023,
        children: [
      {
        name: "换料第一组",
        key: "换料第一组",
        type: "换料",
        time: 2023,
      }
    ]
      }
    ]
  },
  {
    name: "某1电厂",
    key: "某电厂",
    type: "电厂",
    time: 2025
  },
  {
    name: "某2电厂",
    key: "某2电厂",
    type: "电厂",
    time: 2028
  },
]

const rowSelection = {
  onChange: (selectedRowKeys, selectedRows) => {
    console.log(`selectedRowKeys: ${selectedRowKeys}`, 'selectedRows: ', selectedRows);
  },
  onSelect: (record, selected, selectedRows) => {
    console.log(record, selected, selectedRows);
  },
  onSelectAll: (selected, selectedRows, changeRows) => {
    console.log(selected, selectedRows, changeRows);
  },
};

export default {
  data() {
    return {
      data,
      rowSelection,
      columns,
    };
  },
};
</script>
```
