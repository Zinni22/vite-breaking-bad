<script>

import HeaderApp from './components/HeaderApp.vue';
import MainApp from './components/MainApp.vue';

export default {
  
  data() {
    return {
    }
  },

  components:{
    HeaderApp,
    MainApp,
  },


}

</script>

<template>

  <HeaderApp />

  <MainApp />


</template>

<style lang="scss">
@import './styles/main.scss';
</style>
