<script>
import { store } from '../../data/store'
import PokemonCard from './PokemonCard.vue'
import ButtonsPage from '../utilities_components/ButtonsPage.vue'
export default {
    name: 'CardsList',
    data() { return { store } },
    props: { type: Array },
    components: { PokemonCard, ButtonsPage },
    emits: ['button-clicked'],
    methods: {
        onButtonClick(n) {
            this.$emit('button-clicked', n)
        }
    }
}
</script>
<template>
    <!-- POKEMON CARDS LIST -->
    <ul class="row-cols-sm-3 row row-cols-lg-5 justify-content-center">
        <pokemon-card v-for="pokemon in store.pokemons" :key="pokemon._id" :name="pokemon.name" :type="pokemon.type1"
            :img="pokemon.imageUrl" :weight="pokemon.weight">
        </pokemon-card>
        <ButtonsPage @button-clicked="onButtonClick"></ButtonsPage>
    </ul>
</template>