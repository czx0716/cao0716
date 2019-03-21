<template>
    <div>
        <ul class="container">
            <li v-for="(obj,index) in movieList" :key="index">
                <img :src="obj.images.small" alt="">
                <div class='info'>
                    <h3>{{obj.title}}</h3>
                    <br>
                    <p class="actors">
                        演员名：<span v-for="(actor,index) in obj.casts" :key="index">{{actor.name}} </span>
                    </p> 
                    <p>
                        年份：<span>{{obj.year}} </span>
                    </p>
                    <p>
                        导演：<span v-for="(daoyan,index) in obj.directors" :key="index">{{daoyan.name}} </span>
                    </p>
                    <p>
                        类型：<span v-for="(aa,index) in obj.genres" :key="index">{{aa}} </span>
                    </p>
                    <p>
                        浏览次数：<span>{{obj.collect_count}} </span>次观看
                    </p>
                </div>

            </li>
        </ul>
    </div>
</template>


<script>
    import Axios from "axios";
   export default {
       data(){
           return {
               movieList:[]
           }
       },
       created () {
           Axios.get("https://bird.ioliu.cn/v1?url=https://api.douban.com/v2/movie/in_theaters?city=广州&start=0&count=15")
           .then((result)=>{
               this.movieList=result.data.subjects;
           })
           .catch();
       }
}
</script>
<style scoped>
.container{
    padding: 0.2rem;
}
li{
    display: flex;
    padding-bottom: 0.1rem;
    margin-bottom: 0.1rem;
    border-bottom: 1px solid #000;
}
li img{
    width: 90px;
    height: 123px;
}
.info{
    flex-grow: 1;
    margin-left: 0.2rem;
}
.actors{
    width: 175px;
    white-space: nowrap;
    text-overflow: ellipsis;
    overflow: hidden;
}
</style>
