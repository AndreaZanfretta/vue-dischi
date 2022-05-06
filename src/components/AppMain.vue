<template>
    <main>
        <div class="container">
            <div class="row">
                <div v-for="(disco, index) in dischi" :key="index" class="col-6 col-md-4 col-lg-2">
                    <app-card :disco="disco"/>
                </div>
            </div>
        </div>
    </main>
</template>

<script>
import AppCard from './AppCard.vue';
import axios from 'axios';

export default {
    name: 'AppMain',
    components:{
        AppCard,
    },
    data(){
        return{
            dischi: [],
            endPoint: "https://flynn.boolean.careers/exercises/api/array/",
        }
    },
    mounted(){
        axios.get(`${this.endPoint}music`)
        .then(res => {
            this.dischi = res.data.response;
            console.log(this.dischi)

        })
        .catch(err => {
            console.error(err); 
        })
    }
    
}
</script>

<style scoped lang="scss">
@import "./public/styles/generals";
@import "./public/styles/vars";
main{
    width: 100%;
    height: calc(100vh - 80px);
    background-color: $main-bg;
}
.container{
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
</style>