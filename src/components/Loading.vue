<template>
   <div class="loading">
       <img src="../../static/images/dt .gif" alt="">
    </div> 
</template>
<script>
export default {
   name:'Loading',
   data(){
       return{
           msg:''
       }
   } 
}
</script>
<style scoped lang="scss">
  @import '../assets/sass/base.scss';
  	img{
		width: 100%;
		margin-top: rem(10px);
	}

</style>


