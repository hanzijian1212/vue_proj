<template>
    <div>
        <div v-if="kk==1">
           <GoodList :goodId="1"></GoodList>
        </div>
        <div v-else-if="kk==2">
            <GoodList :goodId="2"></GoodList>
        </div>
        <div v-else>
            <GoodList :goodId="0"></GoodList>
        </div>

    </div>
</template>
<script type="text/javascript">
    import Msg from './msg.js'
    import GoodList from './goodsList.vue'
    export default{
        data(){
            return{
                kk:0
            }
        },
        mounted:function(){
            var _this=this //等号右边的this代表当前的  _this表示副本
            Msg.$on('val',function(m){
                _this.kk=m; 
            })
        },
        components:{
            GoodList
        }

    }
</script>