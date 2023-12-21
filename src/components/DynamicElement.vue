<template>
  <div class="dynamic-element">
    <component :is="element.name" v-bind="element.props" v-if="element && element.model" v-model="element.model">
      <template v-if="element.slot" v-slot>{{ element.slot }}</template>
    </component>
    <component :is="element.name" v-bind="element.props" v-else>
      <template v-if="element.name === 'ElTable'" v-for="(column, index) in element.column">
        <el-table-column :prop="column.prop" :label="column.label">
          <template v-if="column.slot" v-slot="scope">{{ scope.row[column.prop] }}</template>
        </el-table-column>
      </template>
      <template v-if="element.slot" v-slot>{{ element.slot }}</template>
    </component>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  element: {
    type: Object,
    required: true
  }
});

</script>

<style lang="scss" scoped>
  .dynamic-element {
    margin: 5px;
  }
</style>
