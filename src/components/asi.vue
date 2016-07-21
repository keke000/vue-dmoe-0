<script>
export default {
    data() {
            return {
                item: {
                    'title': '',
                    'img': '',
                    'id': ''
                },
                lists: {}
            }
        },
        asyncData: function(resolve, reject) {
            var self = this;
            setTimeout(function() {
                self.lists = JSON.parse(localStorage.foodlists);
                var cc = Math.round(Math.random() * (self.lists.length - 1));
                resolve({
                    item: self.lists[cc]
                })


            }, 1000)
        },
        methods: {
            goback: function(e) {
                history.go(-1);
            },
            reAsi: function(id) {
                //var lists = JSON.parse(localStorage.lists);
                var cc = Math.round(Math.random() * (this.lists.length - 1));
                if(this.lists[cc].id == id){
                    return this.reAsi(id);
                }else{
                    this.$data.item = this.lists[cc];
                }
            }

        }
}
</script>
<template>
    <div class="row wrap">
        <div class="col-sm-2" style=" margin-top: 40px">
            <button class="btn btn-info" @click="goback">
                <i class='glyphicon glyphicon-menu-left'></i>
            </button>
        </div>
        <div class="col-sm-8">
            <h1>欢迎来到土豪的菜馆</h1>
        </div>
        <div class="col-sm-2"style=" margin-top: 40px;text-align:right">
            <button class="btn btn-success" v-link="{path: '/'}" >去首页</button>
        </div>
    </div>
    <div class="asi-page">
        <div class="loading" v-if="$loadingAsyncData">
            <div class="spinner">
                <div class="double-bounce1"></div>
                <div class="double-bounce2"></div>
            </div>
            <span>给我一点时间...</span>
        </div>
        <div v-if="!$loadingAsyncData" class="asi-box">
            <ul class='foodlist clearfix'>
                <li >
                    <img :src="'/src/assets/img/test'+item.img+'.jpg'" height="500" width="333">
                    <p>{{item.title}}</p>
                </li>
                <li >
                   <button @click="reAsi(item.id)" class="btn btn-success">我不要吃这个</button>
                </li>
            </ul>
        </div>
    </div>
</template>
