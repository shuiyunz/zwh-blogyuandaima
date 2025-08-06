<script setup>

</script>


<template>
<div class="shemei">

  <ul>
    <a href="https://github.com/shuiyunz/" target="_blank"><li><img src="../../assets/img/shemei/github.png" alt=""></li></a>
    <a href="https://www.douyin.com/user/MS4wLjABAAAAsMlaJiyz066JdIcNNaORuOOSnyF6aGDHoJuDvu8cKXI/search/1933836742?type=user" target="_blank"><li><img src="../../assets/img/shemei/douying.jpg" alt=""></li></a>
    <a href="https://search.bilibili.com/upuser?keyword=uid%EF%BC%9A174830650&from_source=webtop_search&spm_id_from=333.1387&search_source=5" target="_blank"><li><img src="../../assets/img/shemei/bilibili.png" alt=""></li></a>
    <a href="https://weibo.com/u/7497756922" target="_blank"><li><img src="../../assets/img/shemei/weibo.webp" alt=""></li></a>
    <a href="https://www.kuaishou.com/search/author?searchKey=4579958464" target="_blank"><li><img src="../../assets/img/shemei/kuaishou.png" alt=""></li></a>
    <a href="https://www.xiaohongshu.com/search_result?keyword=832317971&source=web_user_page" target="_blank"><li><img src="../../assets/img/shemei/xiaohongshu.png" alt=""></li></a>
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