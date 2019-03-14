<template>
  <div class="list">
      <!-- <loading></loading> -->
    <ul class="items">
      <li class="item" v-for="item in items">
        <img  v-lazy="item.author.avatar_url" alt="">
        <div class="tab">
          <div v-if="item.top" class="top">置顶</div>
          <div v-else-if="item.good" class="top">精华</div>
          <div v-else>{{tab[item.tab]}}</div>
        </div>
        <router-link class="title" :to="'/index/show/'+item.id" tag="div">{{item.title}}</router-link>
      </li>
      <!-- <li class="item">last</li> -->
    </ul>
  </div>
</template>

<script>
import loading from '@/components/loading';
// 引入 axios 模块（封装的ajax）
export default {
  name: 'List',
  data () {
    return {
      // 话题数据
      // 分类的信息
      tab:{
        share:'分享',
        job:'招聘',
        weex:'weex',
        ask:'问答'
      }
    }
  },
  props:['items'],
  
  components:{
    loading
    
  }
}
</script>

<style scoped lang="scss">
  // 引入基础的样式
  @import '../../assets/sass/base.scss';
  // 引入 栏目列表的 样式
  @import '../../assets/sass/itemlist.scss';
</style>
