 <script type="text/javascript">
     
     export default{
        data(){ return {foodsname:''}},
        props: ['boxdata'],
        methods:{
          close: function(){
            this.$dispatch('closemodulebox')
          },
          addfoods: function(){
            if(this.foodsname){
              this.$dispatch('addfoods',this.foodsname)
              this.foodsname = ''
            }
          },
          delfoods: function(id){
            this.$dispatch('delfoods',id)
          }
        }
     }
 </script>
<style type="text/css">
    .modal{
        width: 600px;
        background-color: #fff;
        margin:0 auto;
        bottom: auto;
        top:200px;
    }
    input{
      width: 540px;
      height: 40px;
      padding-left: 12px;
    }
    .modalbox h3{
      font-size: 18px;
    }
</style>
<template>
<div class="modalbox" v-if="boxdata.show">
  <div class="modal fade in" style="display:block"  >
    <div class="modal-header">
      <button type="button" class="close" @click="close" data-dismiss="modal" aria-hidden="true">&times;</button>
      <h3>{{boxdata.title}}</h3>
    </div>
    <div class="modal-body" v-if="boxdata.input">
        <input type="text" v-model="foodsname" placeholder="请输入你想吃的食物" >
    </div>
    <div class="modal-footer">
      <a href="javascript:;" @click="close" class="btn">关闭</a>
      <a href="javascript:;" @click="addfoods" v-if="!boxdata.id" class="btn btn-primary">添加</a>
      <a href="javascript:;" @click="delfoods(boxdata.id)" v-if="boxdata.id" class="btn btn-primary">删除</a>
    </div>
  </div>
<div class="modal-backdrop fade in"></div>
</div>
</template>