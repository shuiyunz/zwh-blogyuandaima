<script setup>

  import { ElCarousel, ElCarouselItem } from 'element-plus'
  import { ref } from 'vue';

  import img1 from '../../assets/img/lunbotu/多层神经网络结构示意图.png'

  import img2 from '../../assets/img/lunbotu/轴突“珍珠串”显微图像.webp'

  import img3 from '../../assets/img/lunbotu/虚拟现实.jpg'

  import img4 from '../../assets/img/lunbotu/人机.webp'

  import img5 from '../../assets/img/lunbotu/回望地球.jpg'



  const imgs = ref([img1,img2,img3,img4,img5])


</script>

<template>

<div class="lbt">
  <div class="block text-center">
    <el-carousel class="rongqi">
      <!-- 修改 v-for 循环为遍历数组索引 -->
      <el-carousel-item v-for="(_, index) in imgs" :key="index" class="rongqi2">
         <div class="tupian">
          <!-- 修正图片绑定方式 -->
          <img :src="imgs[index]" alt="">
         </div>
      </el-carousel-item>
    </el-carousel>
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
    text-decoration: none;
    color: black;
  }

  .lbt {
    width: vw(500);
    height: vw(400);
    // background-color: white;
    margin-left: vw(115);
    border-radius: vw(19);
  }

  .rongqi {
    height: vw(400);
    // transition: all 0.1s linear;
    // &:hover {
    //   transform: scale(1.1);
    // }
    border-radius: vw(19);
    .rongqi2 {
      height: vw(400);
     .tupian {
      width: 100%;
      height: 100%;
      // background-color: pink;
      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
      }
      } 
    }
  }

  // .demonstration {
  //   color: var(--el-text-color-secondary);
  // }

  // .el-carousel__item h3 {
  //   color: #475669;
  //   opacity: 0.75;
  //   line-height: 150px;
  //   margin: 0;
  //   text-align: center;
  // }

  // .el-carousel__item:nth-child(2n) {
  //   background-color: #99a9bf;
  // }

  // .el-carousel__item:nth-child(2n + 1) {
  //   background-color: #d3dce6;
  // }


</style>