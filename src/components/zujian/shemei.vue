<script setup>

import { ref } from 'vue'

const img1 = ref('https://ts3.tc.mm.bing.net/th/id/ODF.bYAvaN8MCaSZfP0o7q_Z_w?w=32&h=32&qlt=90&pcl=fffffc&o=6&pid=1.2')
const img2 = ref('https://s1.aigei.com/src/img/png/91/91e73ffa16d34508b5933e068883ad47.png?imageMogr2/auto-orient/thumbnail/!282x282r/gravity/Center/crop/282x282/quality/85/%7CimageView2/2/w/282&e=2051020800&token=P7S2Xpzfz11vAkASLTkfHN7Fw-oOZBecqeJaxypL:FFszZC7EKttL5LaH_Kmq8Q70vPU=')
const img3 = ref('https://s1.aigei.com/src/img/png/64/64517927d75d4c4d940cc31053cf6d42.png?imageMogr2/auto-orient/thumbnail/!282x282r/gravity/Center/crop/282x282/quality/85/%7CimageView2/2/w/282&e=2051020800&token=P7S2Xpzfz11vAkASLTkfHN7Fw-oOZBecqeJaxypL:X1PbTTLqipc3GxmvsRT_TvvF8Qs=')
const img4 = ref('https://s1.aigei.com/src/img/png/95/95df24d64d9a4369b6d7fddad057288e.png?imageMogr2/auto-orient/thumbnail/!282x282r/gravity/Center/crop/282x282/quality/85/%7CimageView2/2/w/282&e=2051020800&token=P7S2Xpzfz11vAkASLTkfHN7Fw-oOZBecqeJaxypL:knqLKBOGqT8ZT7LwV9F3PP0V3g4=')
const img5 = ref('https://s1.aigei.com/src/img/png/a7/a76536035f624f0fb19334c66c73b6cd.png?imageMogr2/auto-orient/thumbnail/!282x282r/gravity/Center/crop/282x282/quality/85/%7CimageView2/2/w/282&e=2051020800&token=P7S2Xpzfz11vAkASLTkfHN7Fw-oOZBecqeJaxypL:rMho9P4QRHJFCFpKC4TW6AQSD3g=')
const img6 = ref('https://s1.aigei.com/src/img/png/ac/acf1db67ec814ae0840d0a5a94dcd1d8.png?imageMogr2/auto-orient/thumbnail/!282x282r/gravity/Center/crop/282x282/quality/85/%7CimageView2/2/w/282&e=2051020800&token=P7S2Xpzfz11vAkASLTkfHN7Fw-oOZBecqeJaxypL:dEv1-PWwS4ddXA0thwN7fLqxvWI=')




</script>


<template>
<div class="shemei">

  <ul>
    <a href="https://github.com/shuiyunz/" target="_blank"><li><img :src="img1" alt=""></li></a>
    <a href="https://www.douyin.com/user/MS4wLjABAAAAsMlaJiyz066JdIcNNaORuOOSnyF6aGDHoJuDvu8cKXI/search/1933836742?type=user" target="_blank"><li><img :src="img2" alt=""></li></a>
    <a href="https://search.bilibili.com/upuser?keyword=uid%EF%BC%9A174830650&from_source=webtop_search&spm_id_from=333.1387&search_source=5" target="_blank"><li><img :src="img3" alt=""></li></a>
    <a href="https://weibo.com/u/7497756922" target="_blank"><li><img :src="img4" alt=""></li></a>
    <a href="https://www.kuaishou.com/search/author?searchKey=4579958464" target="_blank"><li><img :src="img5" alt=""></li></a>
    <a href="https://www.xiaohongshu.com/search_result?keyword=832317971&source=web_user_page" target="_blank"><li><img :src="img6" alt=""></li></a>
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
  }
  .shemei {
    width: vw(250);
    height: vw(150);
    margin-top: vw(47);
    // background-color: pink;
    background: rgba(135, 206, 235, 0.25);
    backdrop-filter: blur(10px); /* 背景模糊 */
    -webkit-backdrop-filter: blur(10px); /* Safari 兼容性 */
    border: 1px solid rgba(255, 255, 255, 0.18);
    // background: rgba(103, 58, 183, 0.3); /* 紫色调 */
    // backdrop-filter: blur(10px);
    // color: white;
    border-radius: vw(19);
    &:hover {
      // transform: scale(1.4);
      // transform: translateY(-10px);
      // box-shadow: 0 15px 30px rgba(0, 0, 0, 0.4);
      cursor: pointer;
    }

    ul {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-content: space-between;
      height: 100%;
      
      li {
        width: vw(65);
        height: vw(65);
        // background-color: yellow;
        border-radius: vw(19);
        transition: transform 0.1s linear;
        &:hover {
          transform: scale(1.2) translateY(-10px);
          box-shadow: 0 15px 30px rgba(0, 0, 0, 0.4);
        }

      }
      img {
        width: vw(65);
        height: vw(65);
        border-radius: vw(19);
      }
    }
  }


</style>