<script setup>

import { onMounted } from 'vue'

import mianleft from "./components/qvyv/mianleft.vue";
import mianright from "./components/qvyv/mianright.vue";
import shemei from "./components/zujian/shemei.vue";

onMounted(() => {
  const randomBgNum = Math.floor(Math.random() * 6) + 1 // 假设有6张背景图
  document.body.style.backgroundImage = `url('src/assets/img/beijing/beijing${randomBgNum}.jpg')`
})


</script>

<template>

  <div class="container">
    <mianleft class="left"></mianleft>
    <mianright class="right"></mianright>
  </div>

</template>

<style>
  body {
    background-image: url('src/assets/img/beijing/beijing1.jpg');
    background-size: cover; /* 图片覆盖整个页面 */
    background-position: center; /* 图片居中显示 */
    background-repeat: no-repeat; /* 不重复平铺 */
    background-attachment: fixed;
    margin: 0;
    /* min-height: 100vh; */
  }


  ::-webkit-scrollbar {
    display: none;
  }
</style>



<style scoped lang="scss">

  @function vw($px) {
    @return calc($px / 1920) * 100vw; 
  }

  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    list-style: none;
  }

    

  // body {
  //   background-image: url('src/assets/img/beijing1.jpg');
  //   background-size: cover; /* 图片覆盖整个页面 */
  //   background-position: center; /* 图片居中显示 */
  //   background-repeat: no-repeat; /* 不重复平铺 */

  // }

  // 普通样式放在媒体查询之前
  .container {
    display: flex;
    position: relative;
    margin: vw(45) auto;
    width: vw(1700);
    height: vw(990);
    // background-color: red;
    .left {
      position: fixed;
      left: vw(45);
      top: vw(45);
      width: vw(850);
      z-index: 999;
    }
    .right {
      margin-left: vw(900);
      width: vw(800);
    }
    
  }
</style>
