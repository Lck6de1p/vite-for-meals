<template>
  <div class="menu-wrapper" :class="{'show': show, 'hide': !show}">
    <h1>自定义菜单</h1>
    <p class="tip">- 菜名间要以空格区分 -</p>
    <div class="textarea-wrapper"><textarea v-model="menuStr"></textarea></div>
    <div class="menu-btn" @click="handleSubmit">确定</div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue'
import { ref, onMounted, computed } from 'vue'

let props = defineProps({
  menuList: Array,
})

const menuStr = ref('') 
const show = ref(true) 
menuStr.value = props.menuList.join(' ')

let emit = defineEmit(["click"])

function handleSubmit() {
  const str = menuStr.value.trim()
  if (str === '') {
    alert('你怕是要饿死自己！')
  }　else {
    show.value = !show.value
    let arr = str.split(' ')
    setTimeout(() => {
      emit('updateMenu', arr)
      show.value = !show.value
    }, 500);
  }
}

</script>


<style lang="scss" scoped>
.menu-wrapper {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 300px;
  // height: 450px;
  padding: 8px;
  border-radius: 5px;
  background-color: #fff;
  h1, p {
    text-align: center;
  }
  .tip {
    margin: 8px 0;
  }
  .textarea-wrapper {
    height: 300px;
    padding: 8px;
    border: 1px solid black;
    border-radius: 4px;
  }
  textarea {
    width: calc(100%);
    height: 100%;
    resize: none;
    font-size: 16px;
    border: none;
  }
  .menu-btn {
    width: 100%;
    margin: 12px auto;
    font-size: 16px;
    color: #fff;
    line-height: 30px;
    text-align: center;
    border-radius: 5px;
    background-color: #09f;
  }
}

.show {
  animation: show 500ms forwards;
}
.hide {
  animation: hide 500ms forwards;
}
@keyframes show {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
@keyframes hide {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}
</style>

