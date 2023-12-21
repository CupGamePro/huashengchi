<template>
  <div class="container">
    <Header />
    <div class="main-area">
      <LeftBox />
      <Content />
      <RightBox />
    </div>
  </div>
</template>

<script setup>
import Header from './Header.vue';
import LeftBox from './LeftBox.vue';
import Content from './Content.vue';
import RightBox from './RightBox.vue';

</script>

<style lang="scss" scoped>
.container {
  height: 100%;
  width: 100%;
  box-sizing: border-box;;
}
.main-area {
  display: flex;
  height: 100%;
  width: 100%;
  box-sizing: border-box;
}
</style>