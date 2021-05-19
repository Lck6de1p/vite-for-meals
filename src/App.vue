<template>
  <!-- <HelloWorld msg="Hello Vue 3 + Vite" /> -->
  <div class="container">
    <!-- <textarea v-model="mealStr"></textarea> -->
    <div 
      v-for="ball in ballArr" 
      :key="ball.name" 
      class="mealName temp" 
      :style="{top: ball.top , left: ball.left, fontSize: ball.fontSize}
    ">{{ball.name}}</div>
  </div>
</template>

<script setup>
import { ref, onMounted, nextTick } from 'vue'
const mealStr = ref('馄饨 烩面 热干面 刀削面 油泼面 炸酱面 炒面 重庆小面 米线 酸辣粉 土豆粉 螺狮粉 凉皮儿 麻辣烫 肉夹馍 羊肉泡馍 炒饭 盖浇饭 烤肉饭 黄焖鸡米饭 麻辣香锅 火锅 酸菜鱼 烤串 披萨 烤鸭 汉堡 炸鸡 寿司 煎饼果子 南瓜粥 小龙虾 牛排 砂锅 大排档 馒头 西餐 自助餐 小笼包 水果 西北风 烧烤 泡面 水饺 日本料理 涮羊肉 兰州拉面 肯德基 面包 臊子面 小笼包 麦当劳 沙县小吃 烤鱼 海鲜 铁板烧 韩国料理 甜点 鸭血粉丝汤')
const mealArr = ref([])
const ballArr = ref([])
const clientHeight = ref(0)
const clientWidth = ref(0)

onMounted(() => {
  const dom = document.getElementsByClassName('container')[0]
  clientWidth.value = dom.clientWidth
  clientHeight.value = dom.clientHeight
  // random()
})

function random() {
  
  setInterval(() => {
    const mealArr = mealStr.value.split(' ')
    const len = mealArr.length
    ballArr.value.push({
      top: parseInt(Math.random() * clientHeight.value) + 'px',
      left: parseInt(Math.random() * clientWidth.value) + 'px',
      name: mealArr[parseInt(Math.random() * len)],
      fontSize: 12 + parseInt(Math.random() * 20) + 'px'
    })

  }, 200)
  setInterval(() => {
    ballArr.value.shift()
  }, 1000)
}
</script>

<style lang="scss" scoped>
.container {
  position: relative;
  width: 100vw;
  height: 100vh;
  overflow: hidden;
}
.temp {
  position: absolute;
  color: #666;
  font-weight: 500;
  animation: disappear 1000ms;
}
@keyframes disappear {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}

</style>
