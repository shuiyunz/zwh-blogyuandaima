<script setup>  
import { ref } from 'vue'

import fangda from '@/assets/img/shouji/放大.png'
import suoxiao from '@/assets/img/shouji/缩小.png'

// 添加响应式变量控制图片和缩放状态
const currentImage = ref(fangda)
const isZoomed = ref(false)

function qiehuan() {
  // 切换缩放状态
  isZoomed.value = !isZoomed.value
  // 根据状态切换图片
  currentImage.value = isZoomed.value ? suoxiao : fangda
}

</script>

<template>
<div class="pyq1">
  <div class="tu">
    <img :src="currentImage" alt="" @click="qiehuan()">
  </div>
</div>
<div class="pyq2" v-if="isZoomed">
  <div class="top">
    <div class="wuyong"></div>
    <div class="wenben">动态</div>
    <div class="guanbi">
      <img :src="currentImage" alt="" @click="qiehuan()">
    </div>
  </div>
  <div class="bottom">
    <p>暂无</p>
  </div>
</div>
</template>

<style scoped  lang="scss">

  @function vw($px) {
    @return calc($px / 1920) * 100vw; 
  }
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    list-style: none;
  }

  .pyq1 {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    width: vw(185);
    height: vw(400);
    // background-color: white;
    background: rgba(242, 246, 247, 0.25);
    backdrop-filter: blur(10px); /* 背景模糊 */
    -webkit-backdrop-filter: blur(10px); /* Safari 兼容性 */
    border: 1px solid rgba(255, 255, 255, 0.18);
    margin-left: vw(16);
    border-radius: vw(19);
    .tu {
      width: vw(150);
      height: vw(150);
      // background-color: skyblue;
      img {
        width: vw(150);
        height: vw(150);
      }
    }
  }
  .pyq2 {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      // 移除transform: scale(2.5)，改用直接尺寸放大
      width: vw(462.5); // 185 * 2.5
      height: vw(1000); // 400 * 2.5
      background-color: white;
      // margin-left: vw(16);
      border-radius: vw(47.5); // 19 * 2.5
      z-index: 999;
      overflow: scroll; // 按需保留
      .top {
          display: flex;
          justify-content: space-between; // 改为两端对齐
          align-items: center;
          padding: 0 vw(20); // 添加内边距
          width: 100%;
          height: vw(75); // 30 * 2.5
          background-color: whitesmoke;
          .wuyong {
              width: vw(50); // 20 * 2.5
              height: vw(50); // 20 * 2.5
          }
          .wenben {
              width: auto; // 自适应宽度
              height: vw(50);
              font-size: vw(25); // 10 * 2.5
              line-height: vw(50);
          }
          .guanbi {
              width: vw(50);
              height: vw(50);
              img {
                  width: vw(50);
                  height: vw(50);
              }
        }
      }
      .bottom {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        align-items: center;
        p {
          width: 100%;
          height: vw(350);
          line-height: vw(350);
          text-align: center;
          font-size: vw(20);
          color: gray;
        }
      }
    }

</style>