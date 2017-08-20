<template>
    <section class='index'>
       <v-swipe :swipeList = "swipeList"></v-swipe>
         <!-- 主页导航start -->
        <v-homeNav></v-homeNav>
        <!-- 主页导航end -->
    
        <!-- 主页内容start -->
        <!-- 主页内容end -->
    </section>
</template>

<script>
import mSwiper from '../swipe/swipe.vue';
import config from '../../js/config.js';
import iHomeNav from './homeNav.vue';
export default {
    data(){
        return{
            'swipeList':[]
        }
    } ,
    methods:{
        getLunbo(){
            let url = config.getHomeLunbo;
            this.$http.get(url).then(rep => {
                let body = rep.body;
                if(body.status == 0){
                    this.swipeList = body.message;

                }
            })
        }
    },
    components:{
        'v-swipe':mSwiper,
        'v-homeNav': iHomeNav,
    },
    created(){
        this.getLunbo();
    }
}
</script>

<style>

</style>
