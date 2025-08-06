<script setup>

import { ref } from 'vue'
import imgone1 from '../../assets/img/xiangmu/个人博客.png'




import imgtwo1 from '../../assets/img/xuexi/xuexi1.webp'
import imgtwo2 from '../../assets/img/xuexi/xuexi2.webp'
import imgtwo3 from '../../assets/img/xuexi/xuexi3.webp'
import imgtwo4 from '../../assets/img/xuexi/xuexi4.webp'
import imgtwo5 from '../../assets/img/xuexi/xuexi5.webp'
import imgtwo6 from '../../assets/img/xuexi/xuexi6.webp'
import imgtwo7 from '../../assets/img/xuexi/xuexi7.webp'
import imgtwo8 from '../../assets/img/xuexi/xuexi8.webp'
import imgtwo9 from '../../assets/img/xuexi/xuexi9.webp'
import imgtwo10 from '../../assets/img/xuexi/xuexi10.webp'
import imgtwo11 from '../../assets/img/xuexi/xuexi11.webp'



const xiangmu = ref([
  {web: '',
  img:  imgone1,
  one: '网站：个人博客',
  two: '作者：水云（self）',
  thr: '简介: 简简单单的个人博客'
  },
])

const xuexi = ref([
  {web: 'https://space.bilibili.com/174830650/favlist?fid=1165669450&ftype=create',
  img:  imgtwo1,
  one: '视频：c语言',
  two: '作者：黑马',
  thr: '时长: 约26小时'
  },
  {web: 'https://space.bilibili.com/174830650/favlist?fid=1165669450&ftype=create',
  img:  imgtwo2,
  one: '视频：html+css',
  two: '作者：黑马',
  thr: '时长: 约44小时'
  },
  {web: 'https://space.bilibili.com/174830650/favlist?fid=1165669450&ftype=create',
  img:  imgtwo3,
  one: '视频：JavaScript',
  two: '作者：黑马',
  thr: '时长: 约60小时'
  },
  {web: 'https://space.bilibili.com/174830650/favlist?fid=1165669450&ftype=create',
  img:  imgtwo4,
  one: '视频：前端框架前置课',
  two: '作者：黑马',
  thr: '时长: 约26小时'
  },
  {web: 'https://space.bilibili.com/174830650/favlist?fid=1165669450&ftype=create',
  img:  imgtwo5,
  one: '视频：python',
  two: '作者：黑马',
  thr: '时长: 约31小时'
  },
  {web: 'https://space.bilibili.com/174830650/favlist?fid=1165669450&ftype=create',
  img:  imgtwo6,
  one: '视频：vue2+vue3',
  two: '作者：黑马',
  thr: '时长: 约51小时'
  },
  {web: 'https://space.bilibili.com/174830650/favlist?fid=1165669450&ftype=create',
  img:  imgtwo7,
  one: '视频：node.js',
  two: '作者：尚硅谷',
  thr: '时长: 约18小时'
  },
  {web: 'https://space.bilibili.com/174830650/favlist?fid=1165669450&ftype=create',
  img:  imgtwo8,
  one: '视频：Linux',
  two: '作者：尚硅谷',
  thr: '时长: 约20小时'
  },
  {web: 'https://space.bilibili.com/174830650/favlist?fid=1165669450&ftype=create',
  img:  imgtwo9,
  one: '视频：git&github',
  two: '作者：尚硅谷',
  thr: '时长: 约6小时'
  },
  {web: 'https://space.bilibili.com/174830650/favlist?fid=1165669450&ftype=create',
  img:  imgtwo10,
  one: '视频：html+css',
  two: '作者：黑马',
  thr: '时长: 约27小时'
  },
  {web: 'https://space.bilibili.com/174830650/favlist?fid=1165669450&ftype=create',
  img:  imgtwo11,
  one: '视频：figma',
  two: '作者：超人电话亭',
  thr: '时长: 约12小时'
  },
  
  

])


const bianlishuzu = ref(xuexi.value)

const bianxiangmu = () => {
  if (bianlishuzu.value !== xuexi.value) {
    // bianlishuzu.value = xiangmu.value
    bianlishuzu.value = xuexi.value
  }
}
const bianxuexi = () => {
  if (bianlishuzu.value !== xiangmu.value) {
    bianlishuzu.value = xiangmu.value
  }
}




</script>

<template>
  <div class="right">
    <div class="tab">
      <div class="xiangmu" @click="bianxiangmu">已学</div>
      <div class="xuexi" @click="bianxuexi">项目</div>
    </div>
    <ul>
      <li v-for="(item,index) in bianlishuzu" :key="index">
        <a :href="item.web">
        <div class="huamian">
          <div class="zhaopian">
            <img :src="item.img" alt="">
          </div>
          <div class="jieshao">
            <div class="one1">{{item.one}}</div>
            <div class="one1">{{item.two}}</div>
            <div class="one1">{{item.thr}}</div>
          </div>
        </div>
        </a>
      </li>

      
    </ul>
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
  .right {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-content: start;
    width: vw(850);
    height: vw(990);
    // background-color: skyblue;
    .tab {
      display: flex;
      // position: sticky;
      // top: vw(60);
      width: vw(265);
      height: vw(65);
      // background-color: skyblue;
      margin-top: vw(15);
      border-radius: vw(19);
      z-index: 99;
      .xiangmu {
        position: relative;
        width: vw(132);
        height: vw(65);
        border-radius: vw(19) 0 0 vw(19);
        background-color: skyblue;
        background: rgba(135, 206, 235, 0.25);
        backdrop-filter: blur(10px); /* 背景模糊 */
        -webkit-backdrop-filter: blur(10px); /* Safari 兼容性 */
        // border: 1px solid rgba(255, 255, 255, 0.18);
        font-size: vw(40);
        line-height: vw(65);
        text-align: center;
        border-right: 1px solid whitesmoke;
        transition: all 0.1s linear;
        z-index: 0;
        &:hover {
          transform: scale(1.2);
          z-index: 1;
          box-shadow: 0 15px 30px rgba(0, 0, 0, 0.4);
          cursor: pointer;
        }
      }
      .xuexi {
        position: relative;
        top: 0;
        left: 0;
        width: vw(133);
        height: vw(65);
        border-radius: 0 vw(19) vw(19) 0;
        // background-color: skyblue;
        background: rgba(135, 206, 235, 0.25);
        backdrop-filter: blur(10px); /* 背景模糊 */
        -webkit-backdrop-filter: blur(10px); /* Safari 兼容性 */
        // border: 1px solid rgba(255, 255, 255, 0.18);
        font-size: vw(40);
        line-height: vw(65);
        text-align: center;        
        border-left: 1px solid whitesmoke;
        transition: all 0.1s linear;
        z-index: 0;
        &:hover {
          transform: scale(1.2);
          z-index: 1;
          box-shadow: 0 15px 30px rgba(0, 0, 0, 0.4);
          cursor: pointer;
        }
      }
    }
    ul {
      li {
        width: vw(795);
        height: vw(130);
        // background-color: skyblue;
        border-radius: 19px;
        margin-top: vw(65);
        transition: all 0.1s linear;
        &:hover {
          transform: scale(1.2);
          box-shadow: 0 15px 30px rgba(0, 0, 0, 0.4);
        }
        a {
        display: block;
        width: vw(795);
        height: vw(130);
        // background-color: skyblue;
        margin-top: vw(65);
        border-radius: vw(19);
        .huamian {
          display: flex;
          flex-wrap: wrap;
          align-items: center;
          width: vw(795);
          height: vw(130);
          // background-color: skyblue;
          background: rgba(135, 206, 235, 0.25);
          backdrop-filter: blur(10px); /* 背景模糊 */
          -webkit-backdrop-filter: blur(10px); /* Safari 兼容性 */
          border: 1px solid rgba(255, 255, 255, 0.18);
          border-radius: vw(19);
          .zhaopian {
            width: vw(180);
            height: vw(100);
            // background-color: pink;
            border-radius: vw(19);
            margin-left: vw(20);
            img {
              // width: vw(100);
              height: vw(100);
              border-radius: vw(19);
            }
          }
          .jieshao {
            display: flex;
            flex-wrap: wrap;

            margin-left: auto;
            width: vw(400);
            height: vw(100);
            // background-color: pink;
            margin-right: vw(100);
            .one1 {
              width: vw(400);
              height: vw(20);
              margin-bottom: vw(20);
              font-size: vw(20);
              line-height: vw(20);
              // background-color: red;
            }
          }
        }
        }
      }
    }
  }
  
</style>
 
 
 
 
 
 
 
 
 
 
