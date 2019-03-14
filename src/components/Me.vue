<template>
  <div class="me">
    <div class="title">轮播图</div>
		<div class="play">
    <div class="swiper-container">
    <div class="swiper-wrapper">
      <div class="swiper-slide"><img src="../../static/images/1.jpg" alt=""></div>
      <div class="swiper-slide"><img src="../../static/images/2.jpg" alt=""></div>
      <div class="swiper-slide"><img src="../../static/images/3.jpg" alt=""></div>
      <div class="swiper-slide"><img src="../../static/images/4.jpg" alt=""></div>
    </div>
    <!-- Add Pagination -->
    <div class="swiper-pagination"></div>
  </div>	
		</div>
  </div>
</template>


<script>
import Swiper from 'swiper';
import 'swiper/dist/css/swiper.min.css'
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
   mounted: function () {
    // 请求主题列表数据
    var swiper=new Swiper('.swiper-container',{
      pagination:{
        el:'.swiper-pagination',
        clickable:true,
      },
    });

  },
}
</script>

<style scoped lang="scss">
@import '../assets/sass/base.scss';
.me {
  width:rem(720px);
  margin:rem(100px) auto;
  .title{
    text-align: center;
    line-height: rem(100px);
    font-size: rem(40px);
  }
  .play{
    img{
      width: 100%;
    }
  }
  
}
</style>

