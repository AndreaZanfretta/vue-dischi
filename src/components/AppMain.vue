<template>
    <main>
        <div class="container">
            <app-search @search="setSearchText($event)" @searchArtist="setSearchArtist($event)" :genere="genres" :artisti="artists" />
            <div class="row">
                <app-loader v-if="loading" />
                <div v-for="(disco, index) in dischiFiltered" :key="index" class="col-6 col-md-4 col-lg">
                    <app-card :disco="disco"/>
                </div>
            </div>
        </div>
    </main>
</template>

<script>
import AppCard from './AppCard.vue';
import AppLoader from './AppLoader.vue';
import AppSearch from './AppSearch.vue';
import axios from 'axios';

export default {
    name: 'AppMain',
    components:{
        AppCard,
        AppLoader,
        AppSearch,
    },
    data(){
        return{
            dischi: [],
            genres: [],
            artists: [],
            searchGenre: '',
            searchArtist: '',
            endPoint: "https://flynn.boolean.careers/exercises/api/array/",
            loading: false,
            
        }
    },
    methods: {
        setSearchText(text){
            this.searchGenre = text;
            console.log(this.searchGenre)
        },
        setSearchArtist(text){
            this.searchArtist = text;
            console.log(this.searchArtist)
        },
        

    },
    computed: {
        dischiFiltered (){
            return this.dischi.filter((el) =>{
                if(el.genre.toLowerCase().includes(this.searchGenre.toLowerCase())){
                    if(el.author.toLowerCase().includes(this.searchArtist.toLowerCase())){
                        console.log(el.author)
                        return el;
                    }
                }
            })
        },
        /* dischiFiltered (){
            if(this.searchGenre === '' && this.searchArtist === ''){return this.dischi;}
            return this.dischi.filter((el => {
                if((this.searchArtist === '' && this.searchGenre !== '') || this.searchGenre !== ''){
                    return el.genre === this.searchGenre;
                }else if((this.searchArtist !== '' && this.searchGenre === '') || this.searchArtist !== '' ){
                    return el.author === this.searchArtist;
                }
                
            }))
        }, */

    },
    mounted(){
        this.loading = true;
        axios.get(`${this.endPoint}music`)
        .then(res => {
            this.dischi = res.data.response;
            this.dischi.forEach((el) =>{
                if(!this.genres.includes(el.genre)){
                    this.genres.push(el.genre)
                }
            })
            this.dischi.forEach((el) =>{
                if(!this.artists.includes(el.author)){
                    this.artists.push(el.author)
                }
            })
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