<template>
    <main>
        <div class="container">
            <div class="row">
                <div v-for="(disco, index) in dischi" :key="index" class="col-6 col-md-4 col-lg">
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
@import "../assets/styles/generals";
@import "../assets/styles/vars";
main{
    width: 100%;
    background-color: $main-bg;
}
.row{
    padding-top: 50px;
}
</style>