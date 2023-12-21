<template>
  <VueDraggable class="dragArea" :list="list" item-key="uuid" :group="{ name: 'people' }">
    <template #item="{ element }">
      <div class="dynamic-element-list">
        <div class="item-action">
          <el-icon>
            <Delete class="delele-button" @click="remove(element)" />
          </el-icon>
        </div>
        <nested-component :list="element.children" v-if="element.name === 'div'" style="min-height: 300px;" />
        <DynamicElement :element="element" v-else />
      </div>
    </template>
  </VueDraggable>
  <PreviewList :list="list" />
</template>

<script setup>
import { ref, onMounted } from 'vue';
import VueDraggable from 'vuedraggable';
import NestedComponent from '../components/NestedComponent.vue';
import eventBus from '../utils/EventBus';
import PreviewList from '../components/PreviewList.vue';
import DynamicElement from '../components/DynamicElement.vue'

const list = ref([])

onMounted(() => {
  eventBus.on('clearPanel', () => {
    list.value = []
  })
})

const remove = (element) => {
  const index = list.value.indexOf(element);
  list.value.splice(index, 1);
};

</script>

<style lang="scss" scoped>
.dragArea {
  box-sizing: border-box;
  height: 100%;
  width: 100%;
  padding: 8px;
}

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
</style>