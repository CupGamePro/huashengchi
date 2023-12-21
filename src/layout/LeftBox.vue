<template>
  <div class="left-box">
    <el-tabs v-model="activeName" type="card">
      <el-tab-pane label="组件" name="component">
        <el-scrollbar wrap-style="height: calc(100vh - 140px)">
          <VueDraggable ref="el" v-model="list1" :animation="150" :group="{ name: 'people', pull: 'clone', put: false }"
            :sort="false" :clone="cloneCom" @change="log" item-key="id" style="display: flex; flex-wrap: wrap;">
            <template #item="{ element }">
              <div class="item-component">
                {{ element.label }}
              </div>
            </template>
          </VueDraggable>
          <VueDraggable ref="el" v-model="list2" :animation="150" :group="{ name: 'people', pull: 'clone', put: false }"
            :sort="false" :clone="cloneCom" @change="log" item-key="id" style="display: flex; flex-wrap: wrap;">
            <template #item="{ element }">
              <div class="item-component">
                {{ element.label }}
              </div>
            </template>
          </VueDraggable>
        </el-scrollbar>
      </el-tab-pane>
      <el-tab-pane label="卡片" name="card">
        <el-scrollbar wrap-style="height: calc(100vh - 140px)">
          
        </el-scrollbar>
      </el-tab-pane>
      <el-tab-pane label="页面" name="page">
        <el-scrollbar wrap-style="height: calc(100vh - 140px)">
          
        </el-scrollbar>
      </el-tab-pane>
    </el-tabs>
  </div>
</template>

<script setup>
import VueDraggable from 'vuedraggable';
import { v4 as uuidv4 } from 'uuid';
import { ref } from 'vue';

const activeName = ref('component');

const list1 = ref([
  {
    name: 'ElButton',
    label: '按钮',
    props: {
      type: 'primary',
    },
    slot: '点我试试'
  },
  {
    name: 'ElInput',
    label: '输入框',
    model: 'feild',
    props: {
      placeholder: '请输入'
    }
  },
  {
    name: 'ElTable',
    label: '表格',
    props: {
      data: [
        { name: 'John', age: 25, address: '123 Street' },
        { name: 'Jane', age: 30, address: '456 Avenue' },
        { name: 'Bob', age: 35, address: '789 Road' }
      ]
    },
    column: [
      {
        prop: 'name',
        label: 'Name'
      },
      {
        prop: 'age',
        label: 'Age'
      },
      {
        prop: 'address',
        label: 'Address'
      }
    ]
  },
  {
    name: 'ElPagination',
    label: '分页',
    props: {
      total: 100,
      pageSize: 10
    }
  }
])

const list2 = ref([
  {
    name: 'div',
    label: 'DIV',
    children: []
  },
])

const log = (evt) => {
  window.console.log(evt);
}

const cloneCom = (el) => {
  if(el.name === 'div') {
    el.children = []
  }
  return {
    ...el,
    children: [],
    uuid: uuidv4()
  }
}
</script>

<style lang="scss" scoped>
.left-box {
  height: calc(100vh - 48px);
  box-sizing: border-box;
  width: 300px;
  border-right: 1px solid #e0e0e0;
  padding: 20px;

  .el-tab-pane {
    overflow-y: auto;
  }

  .item-component {
    width: 100px;
    height: 40px;
    border: 1px dashed var(--el-color-primary);
    margin: 8px;
    line-height: 40px;
    text-align: center;
    cursor: move;
  }
  .item-component:hover {
    background-color: var(--el-color-primary-light-5) ;
  }
}</style>