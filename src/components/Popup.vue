<template>
    <div id="app">
        <div @click="btnfc()">点击弹窗按钮</div>
        <div  v-show="show">
        <div>
            <div @click="hiddenShow()"><a>关闭</a></div>
            <Popupcontent/>
        </div>
    </div>
    </div>
</template>

<script>
import Popupcontent from './Popupcontent.vue';
  export default {
    el:'app',
    data(){
        return{
            show:false,
        }
    },
    components:{
        Popupcontent,
    },
    mounted:function(){

    },
    methods:{
      btnfc:function(){
          var that = this;
          that.show = true;
      },
      hiddenShow:function(){
          var that = this;
          that.show = false;
      }
    
  }
  }
  
</script>