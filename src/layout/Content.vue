<template>
  <el-scrollbar wrap-style="height: calc(100vh - 80px)">
    <div class="content">
      <ContentLayout />
    </div>
  </el-scrollbar>
</template>

<script setup>
import ContentLayout from '../components/ContentLayout.vue';

</script>

<style lang="scss" scoped>
.content {
  height: calc(-80px + 100vh);
  width: calc(100vw - 300px);
  padding: 20px;
  box-sizing: border-box;
  background-color: #fff;
  display: flex;
  flex-wrap: wrap;
}
</style>