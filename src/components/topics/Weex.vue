<template>
  <div class="weex">
     <topic-list :items="items"></topic-list>
     <infinite-loading class="=loading" @infinite="infiniteHandler"></infinite-loading>
  </div>
</template>

<script>
import {getTopicList} from '@/getdata/getTopics.js';
import topicList from '@/components/topics/List';
import InfiniteLoading from 'vue-infinite-loading';
export default {
  name: 'Weex',
  data () {
    return {
      // 话题数据
      items: [],
      page:1
      // 分类的信息
      // tab:{
      //   share:'分享',
      //   job:'招聘',
      //   Weex:'weex',
      //   ask:'问答'
      // }
    }
  },
 mounted: function () {
    // 请求主题列表数据
    getTopicList({tab:'weex'}).then((data)=>{
      this.items = data.data.data;
    });
  },
   methods: {
    infiniteHandler($state) {
      setTimeout(() => {
        // console.log('该去取一下一页数据了');
        getTopicList({tab:'weex',limit:30,page:++this.page}).then((data)=>{
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
.weex{
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

