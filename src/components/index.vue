<script type="text/javascript" >
    import carousel from './carousel.vue'
    export default {
        components:{carousel:carousel},
        data () {
          return {
            titles:['0000000000000000',11111111111,2222222222],
            totalTime: 1.5
          }
        }
  }
</script>
<style type="text/css">
  .index-carousel{
    width: 1110px;
    margin:60px auto;
    height: 240px;
    overflow: hidden;
  }
  .index-carousel .carousel{
      width: 1110px;
      height: 240px;
    }
  .index-carousel img{
      width: 1110px;
      height: 240px;
    }
  h1{
    padding-top: 40px;
    text-align: center;
    font-size: 24px;
  }
</style>
<template>
    <h1>土豪，今天吃什么？</h1>
     <div class="index-carousel">
       <carousel :msg='titles'></carousel>
     </div>
     <div class="row">
         <button v-link='{path : "/list"}' class="btn btn-primary col-sm-3 col-sm-offset-4">赶紧看看去</button>
     </div>
     
</template>

