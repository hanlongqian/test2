<template>
  <div class="ask">
    <topic-list :items="items"></topic-list>
    <infinite-loading class="=loading" @infinite="infiniteHandler"></infinite-loading>
  </div>
</template>

<script>
import {getTopicList} from '@/getdata/getTopics.js';
import topicList from '@/components/topics/List';
import InfiniteLoading from 'vue-infinite-loading';
export default {
  name: 'Ask',
  data () {
    return {
      // 分类的信息
    items:[],
    page:1
    }
  },
mounted: function () {
    // 请求主题列表数据
    getTopicList({tab:'ask'}).then((data)=>{
      this.items = data.data.data;
    });
  },
   methods: {
    infiniteHandler($state) {
      setTimeout(() => {
        // console.log('该去取一下一页数据了');
        getTopicList({tab:'ask',limit:20,page:++this.page}).then((data)=>{
      // this.items = data.data.data;
      this.items=this.items.concat(data.data.data);
      $state.loaded();
        });
      }, 1000);
    },
  },
    components:{
    topicList,InfiniteLoading
  }
}
</script>


<style scoped lang="scss">
@import '../../assets/sass/base.scss';
.ask{
  margin-top: rem(160px);
  margin-bottom: rem(100px);
}
/deep/ .infinite-loading-container[data-v-358985eb] [class^=loading-] {
  display: inline-block;
  margin:5px 0;
  width: 100px;
  height: 100px;
  font-size: 28px;
  line-height: 28px;
  border-radius: 50%;
}
</style>
