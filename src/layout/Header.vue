<template>
  <div class="header">
    <div class="header-left">
       HuaShengChi
    </div>
    <div class="header-right">
       <el-button type="primary" @click="onClearPanel">清除面板</el-button>
    </div>
  </div>
</template>

<script setup>
import eventBus from '../utils/EventBus';


const onClearPanel = () => {
  eventBus.emit('clearPanel');
}

</script>
<style lang="scss" scoped>
  .header {
    position: relative;
    height: 48px;
    width: 100%;
    padding: 0 20px;
    line-height: 48px;
    box-sizing: border-box;
    z-index: 99;
    box-shadow: rgba(55,99,170,.2) 8px 8px 20px 0px, #fff -8px -8px 20px 0px;
    display: flex;
    justify-content: space-between;
    align-items: center
  }
</style>