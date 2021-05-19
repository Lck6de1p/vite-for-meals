<template>
  <div class="ball" :style="{top: ball.top , left: ball.left, fontSize: ball.fontSize}">{{ball.name}}</div>
</template>

<script setup>
import { defineProps} from 'vue'

defineProps({
  ball: Object
})

</script>


<style lang="scss" scoped>
.ball {
  position: absolute;
  font-weight: 500;
  color: #666;
  animation: disappear 3000ms forwards;
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

