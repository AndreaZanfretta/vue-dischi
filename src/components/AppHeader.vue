<template>
    <header>
        <div class="nav">
            <img src="https://www.freepnglogos.com/uploads/spotify-logo-png/spotify-download-logo-30.png" alt="logo">
        </div>
    </header>
</template>

<script>
export default {
    name: 'AppHeader',
}
</script>

<style scoped lang="scss">
@import "../assets/styles/generals";
@import "../assets/styles/vars";
header{
    width: 100%;
    height: 80px;
    background-color: $header-bg;
}
.nav{
    width: 100%;
    height: 100%;

        img{
            height: 100%;
            padding: 10px 20px;
        }
}
</style>