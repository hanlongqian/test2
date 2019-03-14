<template>
  <div class="gzh">
     <img src="../../static/images/ewm.jpg" alt="">
  </div>
</template>

<script>
export default {
  name: 'Gzh',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  mounted:function(){
    console.log(window.innerHTML)
  }

}
</script>

<style scoped lang="scss">
@import '../assets/sass/base.scss';
.gzh img{
  width:rem(700px);
  display: block;
  margin:rem(100px) auto;
  
}
</style>
