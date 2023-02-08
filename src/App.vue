<script>
import axios from 'axios';
import HeaderApp from './components/HeaderApp.vue';
import MainApp from './components/MainApp.vue';
import FooterApp from './components/FooterApp.vue';

export default {
  
  data() {
    return {
      cards: [],
    }
  },

  components:{
    HeaderApp,
    MainApp,
    FooterApp,
  },

  created(){
    //1. recupero le info di axios dopo averlo installato
    axios 
    .get('https://db.ygoprodeck.com/api/v7/cardinfo.php') 
    .then((response) => {
      console.log(response.data.data.slice(0,30));
      this.cards = response.data.data.slice(0,30);
    });
  },

}

</script>

<template>

  <HeaderApp />

  <MainApp :cardList="cards"/>

  <FooterApp />

</template>

<style lang="scss">
@import './styles/main.scss';
</style>
