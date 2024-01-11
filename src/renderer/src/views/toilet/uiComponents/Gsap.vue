<template>
  <div id="gsap" class="gsap">
    <div class="box box1 green"></div>
    <div class="box box2 orange"></div>
    <div class="box box3 grey"></div>
  </div>
</template>

<script setup>
import { onMounted } from 'vue'
import gsap from 'gsap'

onMounted(() => {
  var tl = gsap.timeline()
  //sequenced one-after-the-other
  tl.to('.box1', { duration: 2, x: 100 }) //notice that there's no semicolon!
    .to('.box2', { duration: 1, y: 200 })
    .to('.box3', { duration: 3, rotation: 360 })
})
</script>

<style lang="scss" scoped>
.box {
  display: block;
  width: 100px;
  height: 100px;
}
.green {
  background-color: green;
}
.orange {
  background-color: orange;
}
.grey {
  background-color: grey;
}

.pink {
  background-color: pink;
}
</style>
