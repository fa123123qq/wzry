<template>
    <section class='index'>
       <v-swipe :swipeList = "swipeList"></v-swipe>
    </section>
</template>

<script>
import mSwiper from '../swipe/swipe.vue';
import config from '../../js/config.js';
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
        'v-swipe':mSwiper
    },
    created(){
        this.getLunbo();
    }
}
</script>

<style>

</style>
