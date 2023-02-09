<script>
export default {

  name: 'Charactercard',

  props: {
    character: Object,
  }

}
</script>

<template>

<div>

    <div class="box">
        <img :src="character.card_images[0].image_url" alt="">
        <h5>{{character.name}}</h5>
        <p>{{character.archetype}}</p>
    </div>

</div>
    
 
</template>

<style scoped>

</style>
