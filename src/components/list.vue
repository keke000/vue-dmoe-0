<script>
 import modelbox from './modelbox.vue'
export default {
    components:{modelbox:modelbox},
    data() {
            var foodlists = localStorage.foodlists? JSON.parse(localStorage.foodlists) : [{img:1,title:'澳洲龙虾',id:1},{img:2,title:'北美肥牛',id:2},{img:3,title:'新西兰牧场鲜奶',id:3},{img:4,title:'82年拉菲',id:4},{img:5,title:'333333333333',id:5}];
            var listState = false;
            if (localStorage.foodlists) {
                if (JSON.parse(localStorage.foodlists).length != 0) {
                    foodlists = JSON.parse(localStorage.foodlists);
                    listState = true;
                }
            }

            return {
                foodlists: foodlists,
                siteInfo: {
                    sitename: "去吃啥？"
                },
                itemname: "",
                showAddModal: false,
                showDelModal: false,
                listState: listState,
                tmpid: "",
                addbox: {
                    title:'土豪的菜肴添加',
                    show: false,
                    input:true
                },
                delbox: {
                    title:'土豪确定要删除这道菜？',
                    show: false
                }
            }
        },
    methods:{
        toaddbox: function(){
            this.delbox.show = false
            this.addbox.show = true
        },
        todelbox: function(id){
            this.delbox.show = true
            this.addbox.show = false
            this.delbox.id = id
        },
        goback: function(){
            history.go(-1)
        }
    },
    events: {
        closemodulebox: function(){
            this.delbox.show = false
            this.addbox.show = false
        },
        addfoods:function(foodsname){
            var imgnum = Math.floor(Math.random()*10)
            var len = this.foodlists.length+1
            this.foodlists.push({
                img:imgnum,
                id: len,
                title: foodsname
            })
            this.delbox.show = false
            this.addbox.show = false
            localStorage.foodlists = JSON.stringify(this.foodlists)
        },
        delfoods: function(id){
            for(var i=0; i<this.foodlists.length;i++){
                if(this.foodlists[i].id == id){
                    this.foodlists.splice(i,1)
                }
            }
            this.delbox.show = false
            this.addbox.show = false
            localStorage.foodlists = JSON.stringify(this.foodlists)
        }
    }
 }

</script>
<style type="text/css">
    .wrap{
        width: 1212px;
        margin:0 auto;
    }
    .foodlist{
        width: 1212px;
        margin:20px auto;
        border:1px solid #e5ee55;
        padding:10px 0 40px 0;
    }
    .foodlist li{
        float: left;
        width: 290px;
        height: 555px;
        margin-left:10px;
        margin-top: 20px;
        text-align: center;
        border:1px solid #6e4649;
        overflow: hidden;
        position: relative;
    }
    .foodlist li i{
        font-size: 18px;
        position: absolute;
        top:0px;
        right: 0px;
        color:red;
        cursor: pointer;
        display: none;
    }
    .foodlist li:hover i{
        display: block;
    }
    .foodlist li img{
        width: 290px;
        height: 500px;
    }
    .foodlist li p{
        text-align: center;
        font-size: 16px;
        line-height: 2;
        padding:10px 0;
    }
    .foodlist li .btn{
        margin-top: 250px;
    }
</style>
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
            <button class="btn btn-success" v-link="{path: './asi'}" >随机选择</button>
        </div>
    </div>
    <ul class='foodlist clearfix'>
        <li v-for='item in foodlists'>
            <img :src="'/src/assets/img/test'+item.img+'.jpg'" height="500" width="333">
            <p>{{item.title}}</p>
            <i class="glyphicon glyphicon-remove-circle" @click="todelbox(item.id)"></i>
        </li>
        <li >
            <button @click="toaddbox" class="btn btn-success">添加顶级美食</button>
        </li>
    </ul>
    <modelbox :boxdata = 'delbox'></modelbox>
    <modelbox :boxdata = 'addbox'></modelbox>
</template>
