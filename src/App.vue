<template>
  <div id="app">
    <AppHeader/>
    <AppMain/>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';

export default {
    components: { AppHeader, AppMain }
}
</script>

<style lang="scss" scoped>
@import "./assets/styles/global";

</style>
