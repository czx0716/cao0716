<template>
    <div>
        <aplayer autoplay
  :music="{
    title: 'secret base~君がくれたもの~',
    artist: 'Silent Siren',
    src: 'https://moeplayer.b0.upaiyun.com/aplayer/secretbase.mp3',
    pic: 'https://moeplayer.b0.upaiyun.com/aplayer/secretbase.jpg'
  }"
/>
    </div>
</template>
<script>
import Axios from 'axios';
import Aplayer from 'vue-aplayer';
   export default {
       components: {
           Aplayer
       },
       data(){
               return{
                   music:[]
               }
           },
       created () {
           Axios.get("https://bird.ioliu.cn/v1?url=https://www.showapi.com/api/lookPoint/405")
           .then((result)=>{
               console.log(result);
               this.musicList=result.data.songlist;
           })
           .catch();
       }
    
}
</script>


<style scoped>



</style>


