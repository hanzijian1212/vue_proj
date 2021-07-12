<template>
    <div name="show">
        <ul class="goodList">
            <li v-for="good in list">
                <img v-bind:src="good.img">
                <p>{{good.goodName}}</p>
            </li>
        </ul>
    </div>
</template>

<style type="text/css">
    .goodList li{
        width: 200px;
        height: 200px;
        list-style: none;
        float: left;
        font-size: 9px;
        margin-bottom: 30px;
    }
    .goodList img{
        width: 180px;
        height: 180px;
        background-color: white;
    }
    .goodList p{
        /* line-height: 36px; */
        padding: 10px 0px;
    }
</style>

<script type="text/javascript">
    export default{
        name:"show",
        data(){         //date数据的传输
            var obj=this;
            var url="";
            if(obj.goodId==1){
                    url="json/bjb.json";
                }else if(obj.goodId==2){
                     url="json/shouji.json";
                }else{
                    url="json/bjb.json";
                }
            this.$http.get(url).then(function(res){
                obj.list=res.data;
            })
            return{
                list:[]
            }
        },
        props:{
            goodId:Number
        },
        //监听事件
        watch:{
            goodId(){
                var obj=this;
                var url="";
                if(obj.goodId==1){
                    url="json/bjb.json";
                }else if(obj.goodId==2){
                     url="json/shouji.json";
                }else{
                    url="json/bjb.json";
                }
                this.$http.get(url).then(function(res){
                   obj.list=res.data; 
                })
                return{
                    list:[]
                }
            }
        }
    }
</script>