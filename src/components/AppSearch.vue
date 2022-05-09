<template>
    <div>
    <!-- seleziona genere -->
        <div class="input-group">
           <select aria-placeholder="Seleziona un genere.." v-model="searchText" class="form-select" aria-label="Default select example">
                <option  v-for="(generi, index) in genere" :key="index" :value="generi">{{generi}}</option>
            </select>
            <div class="input-group-append">
                <button @click="search" class="btn btn-outline-secondary" type="button">Cerca</button>
                <button @click="reset" class="btn btn-outline-secondary" type="button">Reset</button>
            </div>
        </div>
        <!-- seleziona artista -->
        <div class="input-group">
            <select placeholder="Seleziona un' artista.." v-model="artist" class="form-select" aria-label="Default select example" >
                <option  v-for="(artista, index) in artisti" :key="index" :value="artista">{{artista}}</option>
            </select>
            <div class="input-group-append">
                <button @click="searchArtist" class="btn btn-outline-secondary" type="button">Cerca</button>
                <button @click="resetArtist" class="btn btn-outline-secondary" type="button">Reset</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'AppSearch',
    data() {
        return{
            searchText: '',
            artist: '',
        }
    },
    methods: {
        reset(){
            this.searchText = '';
            this.$emit('search', this.searchText);
        },
        search(){
            this.$emit('search', this.searchText);
        },
        resetArtist(){
            this.artist = '';
            this.$emit('searchArtist', this.artist);
        },
        searchArtist(){
            this.$emit('searchArtist', this.artist);
        }
    },
    props: ['genere', 'artisti']
}
</script>

<style scoped lang="scss">

</style>