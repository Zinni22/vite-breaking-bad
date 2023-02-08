<script>
import {store} from '../store';
import CharacterCard from './CharacterCard.vue';

export default {

  name: 'MainApp',
  data() {
    return {
      store,
    }
  },

  components:{
    CharacterCard,
}

}
</script>

<template>

    <main>

        <div class="container">

            <!-- SELECT SECTION -->
            <div class="row">
                <div class="col-auto mb-4">
                    <select aria-label="Select status">
                        <option selected value="">Select status</option>
                        <option value="idk">idk</option>
                        <option value="idk">idk</option>
                        <option value="idk">idk</option>
                    </select>
                </div>
            </div>

            <div class="white-container">
                <div class="card-container">

                    <div class="row g-2">

                        <div class="col-2" v-for="card in store.cards">
                            
                            <CharacterCard :character = card />

                        </div>

                    
                    </div>

                </div>
            </div>

        </div>

    </main>
 
</template>

<style lang="scss">

main{
    background-color: #d48f38;
    padding:70px 0;

    select{
        padding: 5px;
        border-radius: 5px;
    }

    .white-container{
        width: 100%;
        padding: 30px;
        background-color: white;

        .card-container{

            .box{
                min-height: 450px;
                background-color: #d48f38;
                text-align: center;
                padding-bottom: 20px;

                img{
                    width: 100%;
                    margin-bottom: 20px;
                }

                h5{
                    color: white;
                }
            }
        }
    }
}

</style>
