<script setup lang="ts">
import { computed, ref } from 'vue'
const props = defineProps(['selectedIndex'])
const dialogVisible = ref(false)
const arrLeaf = [
  19, 21, 32, 21, 25, 26, 26, 23, 21, 12, 30, 20, 21, 25, 24, 23, 19, 20, 20, 15, 15, 16, 15, 16,
  15, 14, 15, 17, 17, 16, 20, 17, 13, 14, 12, 9, 12, 10, 11, 9, 25, 15, 19, 39, 18, 19, 21, 30
]

const arrJ = [
  31.750060889512554, 30.46283101335576, 32.969146824064545, 27.16457202827586, 31.689049063575617,
  25.342638994514786, 30.72974424280776, 28.789948688035587,

  18.648606938331223, 18.216700887095406, 19.06330732856773, 20.339737940343575, 16.194438024556668,
  18.18144074799152, 15.642302232627046, 14.957980130478594, 17.418174465434543, 14.899985996333566,

  14.034460834757736, 11.868970272818602, 21.582130323357028, 15.42098554254082, 12.261690642363023,
  11.970463627038866,

  16.480497527779935, 14.231598816412667, 15.223313043463772, 13.337119463672016,
  17.032776270279072, 16.97273785007902, 16.796049035139266, 16.827442803003056,

  18.353274304922422, 17.12191645526517, 15.299436410070534, 14.993819090303218, 14.540164478955816,
  12.430671960286293, 11.802900917533936, 14.529686593124879,

  21.47282393148049, 15.173966510740541, 12.742634716400392, 15.148931245712562, 14.227477396973377,
  16.28431664316146, 17.396250083681846, 19.097718613392892
]

const urlList = computed(() => {
  return [
    `http://49.235.88.50:8989/images/data/c${props.selectedIndex + 1}.png`,
    `http://49.235.88.50:8989/images/model/c${props.selectedIndex + 1}.png`,
    `http://49.235.88.50:8989/images/enhance/c${props.selectedIndex + 1}.png`
  ]
})
</script>

<template>
  <div class="my-content">
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
      <div class="content-item">
        <span>增强后的结果</span>
        <el-image
          :src="urlList[2]"
          :zoom-rate="1.2"
          :preview-src-list="urlList"
          :initial-index="2"
          fit="cover"
        />
      </div>
    </div>
    <div class="desc">
      <el-button type="primary" @click="dialogVisible = true">点击查看形态学参数估计</el-button>
    </div>
  </div>
  <el-dialog v-model="dialogVisible" title="形态学参数估计" width="30%" modal-class="modal">
    <el-card :body-style="{ padding: '0px' }">
      <el-image
        :src="`http://49.235.88.50:8989/images/genjing/c${selectedIndex + 1}.png`"
        fit="cover"
        class="modal-image"
      />
      <div class="separator"></div>
      <div style="padding: 14px">
        <p class="modal-p">叶片数量: {{ arrLeaf[selectedIndex] }}</p>
        <p>根茎长度: {{ arrJ[selectedIndex] }} cm</p>
      </div>
    </el-card>
  </el-dialog>
</template>

<style scoped lang="less">
.my-content {
  height: 100%;
  position: relative;
}

.content-wrapper {
  display: flex;
  justify-content: center;
  padding: 0 80px;
  max-height: 90%;
  .content-item {
    width: 33%;
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

.desc {
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
}
</style>

<style lang="less">
.modal {
  &-image {
    box-shadow: 0px 2px 2px #f3ecec;
  }

  &-p {
    margin-bottom: 10px;
  }
}
</style>
