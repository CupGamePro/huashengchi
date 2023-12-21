<template>
  <el-drawer
    v-model="drawer"
    title="I am the title"
  >
    <span>Hi, there!</span>
  </el-drawer>
</template>

<script setup>
import { ref } from 'vue';
const drawer = ref(false);
</script>

<style lang="scss" scoped>
</style>