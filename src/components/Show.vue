<template>
  <div class="show">
      <h1 class="title">{{title}}</h1>
      <div class="author">
        <img :src="avatar_url" alt="">
        <p>{{loginname}}</p>
      </div>
      <div class="content" v-html="content">
          <!-- {{data.content}} -->
      </div>
  </div>
</template>

<script>
import {getTopic} from '@/getdata/getTopics.js'; 
export default {
  name: 'Show',
  data () {
    return {
      title:'',
      avatar_url:'',
      loginname:'',
      content:'',
    }
  },
   mounted: function () {
     //获取文章id
     var id=this.$route.params.id;
     getTopic(id).then((data)=>{
        this.title = data.data.data.title;
        this.avatar_url=data.data.data.author.avatar_url;
        this.loginname=data.data.data.author.loginname;
        this.content=data.data.data.content;
     
     })
  },
}
</script>

<style scoped lang="scss">
@import '../assets/sass/base.scss';
.show{
  margin-top: rem(160px);
  margin-bottom: rem(100px);
  .title{
    font-size:rem(30px);
    text-align: center;
    margin-top:rem(100px) auto;
    margin-bottom:rem(50px);
    color:#333;
  }
  .author{
    display: flex;
    justify-content: center;
    align-items: center;
      img{
        width:rem(80px);
        height: rem(80px);
      }
      p{
        font-size:rem(40px);
        color:green;
        margin-left:rem(40px);
      }
  }
  .content{
    width:rem(740px);
    height:rem(20px) auto;
    // color:red; 
    // a{
    //   color:green;
    // }
  }
}

</style>
