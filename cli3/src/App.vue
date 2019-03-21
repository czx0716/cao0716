<template>
  <div id="app">
    <c-header :obj="obj"></c-header>
    <div id="content">
      <router-view></router-view>
    </div>
    <c-footer :menu="menu" @changeBg="color" :color="obj.bgcolor"></c-footer>
  </div>
</template>

<script>
import CHeader from '@/components/CHeader.vue';
import CFooter from '@/components/CFooter.vue';

export default {
  data(){
    return{
      menu:[        {
          path:"/movie",
          name:"电影",
          bgcolor:"#ff0036"
        },
        {
          path:"/music",
          name:"音乐",
          bgcolor:"#e9f460"
        },
        {
          path:"/book",
          name:"图书",
          bgcolor:"#96c2f1"
        },
        {
          path:"/photo",
          name:"图片",
          bgcolor:"#4abce8"
        },
      ],
      obj:
        {
          path:"/movie",
          name:"电影",
          bgcolor:"#ff0036"
        },
    }
  },
  components: {
    CHeader,
    CFooter
  },
  methods:{
    color(obj){
      this.obj=obj
    }
  },
  created () {
    let result = this.menu.filter((obj,index)=>{
      return obj.path==location.pathname;
    });
    if(result.length){
      this.obj = [...result][0];
    }
  }

}
</script>

<style>
#content{
  margin: 1rem 0;
}
</style>