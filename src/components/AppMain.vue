<template>
    <main>
        <div class="container">
            <div class="row">
                <app-loader v-if="loading" />
                <div v-for="(disco, index) in dischi" :key="index" class="col-6 col-md-4 col-lg">
                    <app-card :disco="disco"/>
                </div>
            </div>
        </div>
    </main>
</template>

<script>
import AppCard from './AppCard.vue';
import AppLoader from './AppLoader.vue';
import axios from 'axios';

export default {
    name: 'AppMain',
    components:{
        AppCard,
        AppLoader,
    },
    data(){
        return{
            dischi: [],
            endPoint: "https://flynn.boolean.careers/exercises/api/array/",
            loading: false,
        }
    },
    mounted(){
        this.loading = true;
        axios.get(`${this.endPoint}music`)
        .then(res => {
            this.dischi = res.data.response;
            this.loading = false;

        })
        .catch(err => {
            console.error(err); 
            this.loading = false;
        })  
    }
    
}
</script>

<style scoped lang="scss">
@import "../assets/styles/generals";
@import "../assets/styles/vars";
main{
    width: 100%;
    min-height: calc(100vh - 80px);
    background-color: $main-bg;
}
.row{
    padding-top: 50px;
}
</style>