<template>
    <div class="card-container text-center">
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
@import "../assets/styles/generals";
@import "../assets/styles/vars";
.card-container{
    width: 200px;
    min-height: 385px;
    margin-bottom: 40px;
    background-color: $header-bg;
        img{
            width: 100%;
            padding: 20px 20px;
        }
        #title{
            color: $title-color;
            font-size: 28px;
            font-weight: 700;
            margin-bottom: 10px;
        }
        p{
            margin: 0;
            color: $font-color;
        }
}
</style>