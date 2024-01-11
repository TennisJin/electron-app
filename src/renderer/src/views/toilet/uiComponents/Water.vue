<template>
  <div class="container">
    <div class="c">
      <div class="drop drop1"></div>
      <div class="drop drop2"></div>
      <div class="text-c">
        <h1>Code. Content. Community</h1>
        <p>Both the drops are created using CSS.</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted } from 'vue'

onMounted(() => {})
</script>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@100&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@600&display=swap');

.container {
  height: 300px;
  margin: 0;
  display: grid;
  place-items: center;
  background: linear-gradient(to right, #12c2e9, #c471ed, #f64f59);
  background: #318cfe;
  font-family: 'Montserrat', sans-serif;
}

.c {
  position: relative;
}

.text-c {
  display: grid;
  place-items: center;
  position: relative;
  font-family: 'Poppins', sans-serif;
}

h1 {
  position: relative;
  font-size: 72px;
  color: white;
}

.drop {
  position: absolute;
  height: 200px;
  width: 200px;
  background: #54abfb;
  border-radius: 51% 49% 48% 52% / 62% 44% 56% 38%;
  opacity: 0.8;
  border: 2px solid #3d93ff;
}

.drop::before {
  content: '';
  position: absolute;
  height: 100%;
  width: 100%;
  background: #318cfe;
  border-radius: 51% 49% 48% 52% / 62% 44% 56% 38%;
  box-shadow:
    -20px 30px 16px #1b6cfb,
    -40px 60px 32px #1b6cfb,
    inset -6px 6px 10px #1b6cfb,
    inset 2px 6px 10px #1a74e5,
    inset 20px -20px 22px white,
    inset 40px -40px 44px #a8ceff;
}

.drop::after {
  content: '';
  position: absolute;
  height: 40px;
  width: 40px;
  background: #e6fdfb;
  border-radius: 44% 56% 46% 54% / 36% 50% 50% 64%;
  left: 130px;
  top: 40px;
  box-shadow: 16px 40px 0 -10px white;
  opacity: 0.8;
}

.drop1 {
  left: -100px;
  top: -50px;
}

.drop2 {
  right: -100px;
  bottom: -50px;
  border-radius: 46% 50% 39% 54% / 56% 57% 50% 50%;
}

.drop2::before {
  border-radius: 46% 50% 39% 54% / 56% 57% 50% 50%;
}

p {
  color: white;
  font-size: 20px;
  font-family: 'Montserrat';
}
</style>
