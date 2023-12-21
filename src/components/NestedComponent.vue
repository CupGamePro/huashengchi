<template>
  <VueDraggable class="drag-area" style="min-height: 300px;" item-key="uuid" :list="list" :group="{ name: 'people' }">
    <template #item="{ element }">
      <div class="dynamic-element-list">
        <div class="item-action">
          <el-icon>
            <Delete class="delele-button" @click="remove(element)" />
          </el-icon>
        </div>
        <nested-component :list="element.children" v-if="element.name === 'div'" />
        <DynamicElement :element="element" v-else />
      </div>
    </template>
  </VueDraggable>
</template>
<script setup>
import VueDraggable from 'vuedraggable';
import { computed } from 'vue'
import DynamicElement from './DynamicElement.vue';

const props = defineProps({
  list: {
    type: Array,
  }
})

const remove = (element) => {
  const index = props.list.indexOf(element);
  props.list.splice(index, 1);
};

</script>
<style scoped lang="scss">
.dragArea {
  box-sizing: border-box;
  height: 800;
  width: 100%;
  border: 1px solid #e0e0e0;
  padding: 8px;

  .dynamic-element-list {
    border: 1px dashed var(--el-color-primary);
    margin: 5px;
    padding: 5px;
    position: relative;

    .item-action {
      display: flex;
      justify-content: flex-end;
      position: absolute;
      top: -10px;
      width: 100%;
      right: 5px;
    }

    .delele-button {
      cursor: pointer;
      color: var(--el-color-danger);
    }
  }
}
</style>

