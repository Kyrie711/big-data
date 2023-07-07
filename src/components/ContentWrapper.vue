<script setup lang="ts">
const props = defineProps(['selectedIndex'])
import { computed } from 'vue'

const urlList = computed(() => {
  return [
    `http://49.235.88.50:8989/images/data/c${props.selectedIndex + 1}.png`,
    `http://49.235.88.50:8989/images/model/c${props.selectedIndex + 1}.png`
  ]
})
</script>

<template>
  <div class="content-wrapper">
    <div class="content-item">
      <span>原训练模型</span>
      <el-image
        :src="urlList[0]"
        :zoom-rate="1.2"
        :preview-src-list="urlList"
        :initial-index="0"
        fit="cover"
        style="margin-right: 20px"
      />
    </div>
    <div class="content-item">
      <span>拟合后的结果</span>
      <el-image
        :src="urlList[1]"
        :zoom-rate="1.2"
        :preview-src-list="urlList"
        :initial-index="1"
        fit="cover"
      />
    </div>
  </div>
</template>

<style scoped lang="less">
.content-wrapper {
  margin-right: 200px;
  display: flex;
  justify-content: center;
  flex: 1;
  padding: 0 80px;

  .content-item {
    width: 50%;
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 20px;

    span {
      font-size: 20px;
      font-weight: 500;
      margin-bottom: 20px;
    }
  }
}
</style>
