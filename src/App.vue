<template>
  <div id="app">
    <app-header />
    <app-main />
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue'


export default {
  name: 'App',
  components: {
    AppHeader,
    AppMain,
    
  }
}
</script>

<style lang="scss">
@import "assets/styles/generals";
#app {

}
</style>
