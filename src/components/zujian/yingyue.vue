<script setup>
import { ref, onMounted } from 'vue';

import song1 from '@/assets/MP3/songs/灾.mp3'
import song2 from '@/assets/MP3/songs/Deadman.mp3'
import song3 from '@/assets/MP3/songs/不眠之夜.mp3'
import song4 from '@/assets/MP3/songs/第三十八年夏至.mp3'
import song5 from '@/assets/MP3/songs/夜泊秦淮.mp3'
import song6 from '@/assets/MP3/songs/One Night In Shanghai.mp3'
import song7 from '@/assets/MP3/songs/LOSER.mp3'
import song8 from '@/assets/MP3/songs/茫.mp3'
import song9 from '@/assets/MP3/songs/要你管.mp3'
import song10 from '@/assets/MP3/songs/Baby，Don’t Cry.mp3'

import zanting from '@/assets/img/player/biaoqian/player2.svg'
import bofang from '@/assets/img/player/biaoqian/player3.svg'

const img1 = ref('http://img3.kuwo.cn/star/albumcover/500/72/76/3791206792.jpg')
const img2 = ref('https://img1.kuwo.cn/star/albumcover/500/s4s82/29/3673122490.jpg')
const img3 = ref('http://img1.kuwo.cn/star/albumcover/500/s3s10/34/2157405799.jpg')
const img4 = ref('https://ts1.tc.mm.bing.net/th/id/OIP-C.WoOBLe3i3r_GQwclRlpfWAAAAA?w=108&h=108&c=1&bgcl=a5be44&r=0&o=7&dpr=1.5&pid=ImgRC&rm=3')
const img5 = ref('http://img2.kuwo.cn/star/albumcover/500/83/38/4092414705.jpg')
const img6 = ref('http://img2.kuwo.cn/star/albumcover/500/53/2/2645507855.jpg')
const img7 = ref('http://img4.kuwo.cn/star/albumcover/500/38/52/2979075485.jpg')
const img8 = ref('http://img3.kuwo.cn/star/albumcover/500/87/99/1167291248.jpg')
const img9 = ref('http://img1.kuwo.cn/star/albumcover/500/4/36/1133624302.jpg')
const img10 = ref('https://ts4.tc.mm.bing.net/th/id/OIP-C.fgh6QQbQV-sMATWSR7V_VAHaHa?w=108&h=108&c=1&bgcl=cca172&r=0&o=7&dpr=1.5&pid=ImgRC&rm=3')

// const song1 = ref('https://sp-sycdn.kuwo.cn/e03e3ce35280e664fd53feb3d114ed2c/689349fc/resource/n3/72/23/2714299072.mp3?bitrate$128&from=vip')



  const songs = ref([
        {
          title: "灾",
          artist: "易烊千玺",
          src: song1,
          img: img1,
        },
        {
          title: "Deadman",
          artist: "蔡徐坤",
          src: song2,
          img: img2
        },
        {
          title: "不眠之夜",
          artist: "张杰",
          src: song3,
          img: img3
        },
        {
          title: "第三十八年夏至",
          artist: "河图",
          src: song4,
          img: img4

        },
        {
          title: "夜泊秦淮",
          artist: "Ice Paper",
          src: song5,
          img: img5
        },
        {
          title: "One Night In Shanghai",
          artist: "胡彦斌",
          src: song6,
          img: img6
        },
        {
          title: "LOSER",
          artist: "米津玄师",
          src: song7,
          img: img7
        },
        {
          title: "茫",
          artist: "李润祺",
          src: song8,
          img: img8
        },
        {
          title: "要你管",
          artist: "时代少年团",
          src: song9,
          img: img9
        },
        {
          title: "Baby，Don’t Cry",
          artist: "EXO",
          src: song10,
          img: img10
        },
  ])


  

  function getRandomInt(min, max) {
    return Math.floor(Math.random() * (max - min)) + min;
  }
  const randomNum = getRandomInt(0, 7); // (0,5)结果可能是 0,1,2,3,4




   const audio = new Audio(); // 创建空音频对象
   audio.src = songs.value[randomNum].src;
   audio.preload = 'auto';
  //  audio.play()


   // 添加播放状态响应式变量
   const isPlaying = ref(false)
   const currentImage = ref(bofang)
   
   function tingyvfang() {
      if (audio.paused) {
          audio.play()
          // isPlaying.value = true
          currentImage.value = zanting
      } else {
          audio.pause()
          // isPlaying.value = false
          currentImage.value = bofang
      }
   }

   const currentIndex = ref(randomNum) // 替换 randomNum 为响应式索引

   function huange(n) {
       // 修改为支持两种模式：数字为步长，对象为直接跳转
       let newIndex = typeof n === 'number' ? 
           currentIndex.value + n :  // 步长模式
           n;                        // 直接索引模式
       
       // 边界处理（循环逻辑）
       if(newIndex < 0) newIndex = songs.value.length - 1
       else if(newIndex >= songs.value.length) newIndex = 0
       
       currentIndex.value = newIndex
       
       // 更新音频源
       audio.pause()
       audio.src = songs.value[currentIndex.value].src
      //  audio.currentTime = 0  // 重置播放进度
      tingyvfang()
       
       // 保持播放状态连续性
       if(isPlaying.value) {
           audio.play().catch(error => {
               console.error('播放失败:', error)
               isPlaying.value = false
           })
       }
   }

   // 初始化时使用响应式索引
   audio.src = songs.value[currentIndex.value].src
  //  audio.play()


   audio.addEventListener('ended', () => {
    huange(1)
    if(isPlaying.value) {
        audio.play()
    }
    })

    const gedanRef = ref(null)
    
    function liebiao() {
      // 修复条件判断并添加切换逻辑
      if (getComputedStyle(gedanRef.value).display === 'none') {
        gedanRef.value.style.display = 'block'
      } else {
        gedanRef.value.style.display = 'none'
      }
    }


   </script>
   
   <template>
   
     <div class="yingyue">
       <div class="up">
         <div class="main">
           <div class="left">
             <div class="up2">{{songs[currentIndex].title}}</div>
             <div class="down2">{{songs[currentIndex].artist}}</div>
           </div>
           <div class="right">
             <img :src="songs[currentIndex].img" alt="">
           </div>
         </div>
       </div>
       <div class="down">
         <!-- <div class="shichang">
           <ul>
             <li></li>
             <li></li>
           </ul>
         </div> -->
         <ul>
           <li><img src="../../assets/img/player/biaoqian/player1.svg" class="shangyishou" @click="huange(-1)"></li>
           <li>
               <img :src="currentImage" @click="tingyvfang()">
           </li>
           <li><img src="../../assets/img/player/biaoqian/player4.svg" class="xiaoyishou" @click="huange(1)"></li>
           <li><img src="../../assets/img/player/biaoqian/player5.svg" class="liebiao" @click="liebiao()"></li>
           
         </ul>
       </div>
       <div class="gedan" ref="gedanRef">
        <ul>
          <li v-for="(item,index) in songs" @click="currentIndex = index; huange(0)">
            <div class="xingxi">
              <div class="zuo">
                <div class="geqv">{{item.title}}</div>
                <div class="zuozhe">{{item.artist}}</div>
              </div>
              <div class="you">
                <img :src="songs[index].img" alt="">
              </div>
            </div>
          </li>
        </ul>
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
   
     .yingyue {
       position: relative;
       width: vw(500);
       height: vw(185);
       margin-top: vw(33);
       // background-color: pink;
       background: rgba(135, 206, 235, 0.25);
       backdrop-filter: blur(10px); /* 背景模糊 */
       -webkit-backdrop-filter: blur(10px); /* Safari 兼容性 */
       border: 1px solid rgba(255, 255, 255, 0.18);
       border-radius: vw(19);
       transition: all 0.1s linear;
       transform: translateZ(0);
       will-change: transform;
       z-index: 500;
       &:hover {
         // transform: scale(1.2);
         cursor: pointer;
       }
       .up {
         display: flex;
         flex-wrap: wrap;
         justify-content: center;
         align-items: center;
         width: vw(500);
         height: vw(93);
         // background-color: #fff;
         border-radius: vw(19) vw(19) vw(0) vw(0);
         .main {
         display: flex;
         flex-wrap: wrap;
         justify-content: space-evenly;
         align-items: center;
         width: vw(460);
         height: vw(72);
         border-bottom: 1px solid #434343;
   
         // background-color: skyblue;
         .left {
           width: vw(380);
           height: vw(50);
           // background-color: pink;
           .up2 {
             width: vw(380);
             height: vw(30);
             // background-color: white;
             font-size: vw(24);
             line-height: vw(24);
           }
           .down2 {
             width: vw(380);
             height: vw(20);
             // background-color: pink;
             font-size: vw(14);
             line-height: vw(20);
             color: #434343;
             
           }
         }
         .right {
           width: vw(50);
           height: vw(50);
           // background-color: pink;
           border-radius: 9px;
           img {
             width: vw(50);
             height: vw(50);
             border-radius: vw(9);
           }
         }
         }
       }
       .down {
         display: flex;
         flex-wrap: wrap;
         justify-content: center;
         align-items: center;
         width: vw(500);
         height: vw(93);
         // background-color: skyblue;
         border-radius: vw(0) vw(0) vw(19) vw(19);
         // .shichang {
         //   width: vw(420);
         //   height: vw(22);
         //   background-color: pink;
         //   margin-top: vw(3);
         //   margin-bottom: vw(5);
         // }
         ul {
           display: flex;
           flex-wrap: wrap;
           justify-content: space-between;
           width: vw(420);
           height: vw(30);
           // background-color: yellow;
           transition: all 0.1s linear;
           li {
             width: vw(30);
             height: vw(30);
             // background-color: green;
             img {
               width: vw(30);
               height: vw(30);
             }
             &:hover {
               border-radius: 50%;
               transform: scale(2);
               box-shadow: 0 15px 30px rgba(0, 0, 0, 0.4);
               cursor: pointer;
             }
           }
         }
       }
       .gedan {
        display: none;
        position: absolute;
        // display: flex;
        flex-wrap: wrap;
        justify-content: center;
        top: vw(165);
        left: 0;
        width: vw(500);
        height: vw(280);
        // background-color: skyblue;
        background: rgba(161, 215, 231, 1);
        backdrop-filter: blur(10px); /* 背景模糊 */
        -webkit-backdrop-filter: blur(10px); /* Safari 兼容性 */
        border: 1px solid rgba(255, 255, 255, 0.18);
        border-radius: vw(19);
        z-index: 999;
        overflow: scroll;
        ul {
          width: vw(460);
          height: vw(280);
          li {
            width: vw(460);
            height: vw(72);
            margin-left: vw(20);
            padding: vw(11) vw(10);
            // background-color: red;
            .xingxi {
              display: flex;
              flex-wrap: wrap;
              justify-content: space-between;
              width: vw(440);
              height: vw(50);
              // background-color: pink;
              background: rgba(18, 255, 176, 0.25);
              backdrop-filter: blur(10px); /* 背景模糊 */
              -webkit-backdrop-filter: blur(10px); /* Safari 兼容性 */
              border: 1px solid rgba(255, 255, 255, 0.18);
              transition: all 0.1s linear;
              &:hover {
                transform: scale(1.1);
                background: rgba(191, 116, 153, 0.25);
              }
              .zuo {
                width: vw(380);
                height: vw(50);
                // background-color: skyblue;
                .geqv {
                  width: vw(380);
                  height: vw(30);
                  line-height: vw(30);
                  font-size: vw(24);
                }
                .zuozhe {
                  width: vw(380);
                  height: vw(20);
                  line-height: vw(20);
                  font-size: vw(16);
                  color: #434343;
                }
              }
              .you {
                width: vw(50);
                height: vw(50);
                // background-color: skyblue;
                img {
                  width: vw(50);
                  height: vw(50);
                  border-radius: vw(9);
                }
              }
            }
          }
        }
       }
   
     }
   
     
   </style>