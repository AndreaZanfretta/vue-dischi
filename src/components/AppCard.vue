<template>
    <div class="card-container">
        <img :src="disco.poster" alt="disco.title">
        <p id="title">{{disco.title}}</p>
        <p>{{disco.author}}</p>
        <p>{{disco.year}}</p>
    </div>
</template>

<script>
export default {
    name: 'AppCard',
    props: {
        disco: Object,
    }
}
</script>

<style scoped lang="scss">
@import "./public/styles/generals";
@import "./public/styles/vars";
.card-container{
    width: 200px;
    background-color: $header-bg;
    margin: ;
        img{
            width: 100%;
            padding: 20px 20px;
        }
        #title{
            color: $title-color;
        }
        p{
            margin: 0;
        }
}
</style>