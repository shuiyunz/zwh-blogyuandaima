<script setup>

import shemei from '../zujian/shemei.vue';
import yingyue from '../zujian/yingyue.vue';
import lunbotu from '../zujian/lunbotu.vue';
import shouji from '../zujian/shouji.vue';



</script>

<template>

  <div class="left">
    <div class="up">
      <div class="zuo">
        <div class="touxiang">
          <img src="../../assets/img/touxiang.jpg" alt="">
        </div>
        <div class="gerenjieshao">
        <ul>
          <li>水云</li>
          <li>5.1金牛座</li>
          <li>#真理</li>
          <li>#念头通达</li>
          <li>#人不知而不愠</li>
          <li>#随性所欲而不逾矩</li>
        </ul>
        </div>
        <shemei></shemei>
      </div>
      <div class="you">
        <div class="gerenjieshao"></div>
        <yingyue></yingyue>
        <div class="zhenzaizuo">
          <div class="timu">&nbsp&nbsp&nbsp&nbsp正在做的事：</div>
          <ul>
            <li><a href="https://www.bilibili.com/video/BV1Bq421A74G/?spm_id_from=333.1391.0.0&p=2&vd_source=360ccfe57b98efe54be61f6f6399ddf0" target="_blank">吴恩达《机器学习》</a></li>
            <li><a href="https://space.bilibili.com/1567748478/lists/358497?type=series" target="_blank">李沐《动手学深度学习 PyTorch版》</a></li>
            <li><a href="https://www.bilibili.com/video/BV1BW411n7gw/?spm_id_from=333.1391.0.0&vd_source=360ccfe57b98efe54be61f6f6399ddf0" target="_blank">屈婉玲《离散数学》</a></li>
          </ul>
        </div>
      </div>
    </div>
    <div class="down">
      <shouji></shouji>
      <lunbotu></lunbotu>
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
  .left {
    width: vw(850);
    height: vw(990);
    // background-color: purple;
    .up {
      display: flex;
      width: vw(850);
      height: vw(495);
      // background-color: pink;
      .zuo {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        align-content: flex-start;

        position: relative;
        

        width: vw(283);
        height: vw(495);
        // background-color: red;

        .touxiang {
          position: relative;
          width: vw(250);
          height: vw(250);
          // background-color: pink;
          border-radius: 50%;
          transition: all 0.1s linear;

          &:hover {
            transform: scale(1.4);
            cursor: pointer;
            
          }
          img {
          width: vw(250);
          height: vw(250);
          border-radius: 50%;
          }
          &:hover {
            cursor: pointer;
          }
          
        }


        .gerenjieshao {
          display: none;
          width: vw(505);
          height: vw(495);
          // background-color: skyblue;
          background: rgba(135, 206, 235, 0.25);
          backdrop-filter: blur(10px); /* 背景模糊 */
          -webkit-backdrop-filter: blur(10px); /* Safari 兼容性 */
          border: 1px solid rgba(255, 255, 255, 0.18);
          border-radius: vw(19);
          ul {
            width: vw(505);
            height: vw(495);
            li {
              width: vw(450);
              height: vw(60);
              margin-left: vw(28);
              margin-top: vw(20);
              margin-bottom: vw(20);
              font-size: vw(40);
              line-height: vw(60);
            }
          }
        }

        .touxiang:hover + .gerenjieshao {
          display: block;
          position: absolute;  
          left: vw(315);
          top: vw(0);
          z-index: 999;
          transition: all 0.1s linear;

        }

        // .shemei {
        //   width: vw(250);
        //   height: vw(150);
        //   margin-top: vw(47);
        //   background-color: pink;
        // }
      }
      .you {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        align-content: start;
        position: relative;

        width: vw(567);
        height: vw(495);
        // background-color: green;
        // .yingyue {
        //   width: vw(500);
        //   height: vw(185);
        //   margin-top: vw(33);
        //   background-color: pink;
        //   border-radius: 19px;
        // }
        .zhenzaizuo {
          width: vw(500);
          height: vw(185);
          margin-top: vw(44);
          // background-color: pink;
          background: rgba(135, 206, 235, 0.25);
          backdrop-filter: blur(10px); /* 背景模糊 */
          -webkit-backdrop-filter: blur(10px); /* Safari 兼容性 */
          border: 1px solid rgba(255, 255, 255, 0.18);
          border-radius: vw(19);
          transition: all 0.1s linear;
          z-index: 1;
          &:hover {
            // transform: scale(1.2);
            cursor: pointer;
          }
          .timu {
            width: 100%;
            height: vw(50);
            font-size: vw(40);
            line-height: vw(50);
            border-bottom: 1px solid #434343;
          }
          ul {
            li {
              margin-left: vw(30);
              font-size: vw(30);
              color: #434343;
              transition: all 0.1s linear;
              &:hover {
                backdrop-filter: blur(9px);
                transform: scale(1.1);
                cursor: pointer;
              }
            }
          }
        }
      }
    }
    .down {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      width: vw(850);
      height: vw(495);
      // background-color: red;
      .lbt {
        width: vw(500);
        height: vw(400);
        background-color: white;
        margin-left: vw(115);
        border-radius: vw(19);
      }
    }
  }






  


</style>
 
 
 
 
 
 
 
 
 
