<script>
import axios from 'axios';
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
    },

    methods:{

        changeCard(archetype){
            console.log('ho cambiato carta')

            axios
            .get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=${archetype}`)
            .then((response) => {
                console.log('dopo che ho selezionato', response.data.data.slice(0,30));
                this.store.cards = response.data.data.slice(0,30);
            })
        }

    },

    created(){
        //1. recupero le info delle carte
        axios 
        .get('https://db.ygoprodeck.com/api/v7/cardinfo.php') 
        .then((response) => {
        console.log(response.data.data.slice(0,30));
        this.store.cards = response.data.data.slice(0,30);
        });

        // 2. recupero le info degli archetype
        axios
        .get("https://db.ygoprodeck.com/api/v7/archetypes.php")
        .then ((response) => {
            console.log(response.data.slice(0,30));
            this.store.archetypes = response.data.slice(0,30);
        });
    },

}
</script>

<template>

    <main>

        <div class="container">

            <!-- SELECT SECTION -->
            <div class="row">
                <div class="col-auto mb-4">
                    <select aria-label="Select status"
                    v-model="store.statusValue"
                    @change="changeCard(store.statusValue)">
                        <option selected value="">Select status</option>

                        <option v-for="item in store.archetypes"
                        :value="item.archetype_name">
                            {{item.archetype_name}}
                        </option>

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
