<script setup lang="ts">
defineEmits(['change-index'])
defineProps(['selectedIndex'])
</script>

<template>
  <div class="side-nav-wrapper">
    <el-scrollbar>
      <div v-for="(item, index) in 48" :key="item">
        <p v-if="index === selectedIndex" class="scrollbar-demo-item">模型{{ index + 1 }}</p>
        <div v-else class="scrollbar-item">
          <el-button plain @click="$emit('change-index', index)"> 模型{{ index + 1 }} </el-button>
        </div>
      </div>
    </el-scrollbar>
  </div>
</template>

<style scoped lang="less">
.side-nav-wrapper {
  width: 200px;
  color: var(--el-color-primary);
  margin-left: 100px;
}
.scrollbar-demo-item {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 50px;
  margin: 10px;
  text-align: center;
  border-radius: 4px;
  background: var(--el-color-primary-light-9);
  color: var(--el-color-primary);
}

.scrollbar-item {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 10px;
  text-align: center;

  :deep(.el-button) {
    height: 50px;
    width: 200px;
  }
}
</style>
