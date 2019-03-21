<template>
    <div class="footer" :style="{background:color}">
        <ul>
            <li v-for="(obj,index) in menu" :key="index">
                <router-link :to="obj.path" @click.native="change(obj)">{{obj.name}}</router-link>
            </li>
        </ul>
    </div>
  
</template>

<script>
export default {
    data(){
        return {
            
        }
    },
    props: ["menu","color"],
    methods: {
        change(obj){
            this.$emit('changeBg',obj)
        }
    }
  
  }

</script>

<style scoped>
    .footer{
        position: fixed;
        bottom: 0;
        left: 0;
        height: 1rem;
        width: 100%;
        background: #ff0036;
    }
    .footer ul{
        display: flex;
    }
    li{
        flex-grow: 1;
        color: #fff;
        line-height: 1rem;
        text-align: center;
    }
    .footer a{
        color: #000;
        outline: none;
        
    }
    .footer a.router-link-active{
        color: #fff;
        text-decoration: none;
    }


</style>
