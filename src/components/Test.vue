<template>
  <n-data-table :columns="columns" :data="data" :pagination="pagination" />
</template>

<script lang="ts">
import { defineComponent, h } from 'vue'
import { NEllipsis, EllipsisProps } from 'naive-ui'

const columns = [
  {
    title: 'Name',
    key: 'name'
  },
  {
    title: 'Age',
    key: 'age'
  },
  {
    title: 'Address',
    key: 'address',
    width: 100,
    ellipsis: {
      tooltip: true
    }
  },
  {
    title: 'Another Address',
    key: 'anotherAddress',
    width: 100,
    render(row: any) {
      const ellipsisProps = row.age < 40 && { tooltip: true };
      return h(NEllipsis, ellipsisProps as EllipsisProps, {
        default: () => row.anotherAddress
      })
    }
  }
]

const data = [
  {
    key: 0,
    name: 'John Brown',
    age: 32,
    address: 'New York No. 1 Lake Park',
    anotherAddress: 'New York No. 1 Lake Park'
  },
  {
    key: 1,
    name: 'Jim Green',
    age: 42,
    address: 'London No. 1 Lake Park',
    anotherAddress: 'New York No. 1 Lake Park'
  },
  {
    key: 2,
    name: 'Joe Black',
    age: 32,
    address: 'Sidney No. 1 Lake Park',
    anotherAddress: 'New York No. 1 Lake Park'
  }
]

export default defineComponent({
  setup () {
    return {
      data,
      columns,
      pagination: { pageSize: 10 }
    }
  }
})
</script>
