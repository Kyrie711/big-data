<script setup lang="ts">
import SideNav from './components/SideNav.vue'
import TopNav from './components/TopNav.vue'
import ContentWrapper from './components/ContentWrapper.vue'
import { ref } from 'vue'

const selectedIndex = ref(0)

function changeIndex(index: number) {
  selectedIndex.value = index
}
</script>

<template>
  <div class="wrapper">
    <TopNav />
    <div class="content">
      <SideNav @change-index="changeIndex" :selected-index="selectedIndex" />
      <ContentWrapper :selected-index="selectedIndex" />
    </div>
  </div>
</template>

<style scoped lang="less">
.wrapper {
  height: 100%;
  background-color: #fff;

  .content {
    height: calc(100% - 70px);
    display: flex;
  }
}
</style>
