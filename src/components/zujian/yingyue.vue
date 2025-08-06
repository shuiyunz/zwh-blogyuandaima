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

  const songs = ref([
        {
          title: "灾",
          artist: "易烊千玺",
          src: song1,
          img: "/src/assets/img/player/songs/灾.jpg"
        },
        {
          title: "Deadman",
          artist: "蔡徐坤",
          src: song2,
          img:"/src/assets/img/player/songs/Deadman.jpg"
        },
        {
          title: "不眠之夜",
          artist: "张杰",
          src: song3,
          img:"/src/assets/img/player/songs/不眠之夜.jpg"
        },
        {
          title: "第三十八年夏至",
          artist: "河图",
          src: song4,
          img:"/src/assets/img/player/songs/第三十八年夏至.jpg"
        },
        {
          title: "夜泊秦淮",
          artist: "Ice Paper",
          src: song5,
          img:"/src/assets/img/player/songs/夜泊秦淮.jpg"
        },
        {
          title: "One Night In Shanghai",
          artist: "胡彦斌",
          src: song6,
          img:"/src/assets/img/player/songs/One Night In Shanghai.jpg"
        },
        {
          title: "LOSER",
          artist: "米津玄师",
          src: song7,
          img:"/src/assets/img/player/songs/LOSER.jpg"
        },
        {
          title: "茫",
          artist: "李润祺",
          src: song8,
          img:"/src/assets/img/player/songs/茫.jpg"
        },
        {
          title: "要你管",
          artist: "时代少年团",
          src: song9,
          img:"/src/assets/img/player/songs/要你管.jpg"
        },
        {
          title: "Baby，Don’t Cry",
          artist: "EXO",
          src: song10,
          img:"/src/assets/img/player/songs/Baby，Don’t Cry.jpg"
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
   
   function tingyvfang() {
      if (audio.paused) {
          audio.play()
          isPlaying.value = true
      } else {
          audio.pause()
          isPlaying.value = false
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
               <img 
                   :src="isPlaying ? 'src/assets/img/player/biaoqian/player2.svg' : 'src/assets/img/player/biaoqian/player3.svg'"
                   @click="tingyvfang"
               >
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