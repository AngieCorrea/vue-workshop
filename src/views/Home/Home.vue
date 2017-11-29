<template>
  <default-layout>
    <section slot="filters" class="pokedex-filters mb-5">
      <div class="container">
        <div class="row">
          <div class="col-md-12">
            <div>
              <label>Busca a tu pokemon favorito</label>
              <input
                type="text"
                class="form-control"
                v-model="filter"
                placeholder="Introduce el nombre del pokemon">
              <small id="emailHelp" class="form-text text-muted">Actualmente solo se pueden hacer búsquedas por nombre</small>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section slot="content" class="podexex-items">
      <div class="row">
        <div
          class="col-md-3 mb-3"
          v-for="item in filteredPokemon"
          :key="item.id">
          <pokedex-card :pokemon="item"></pokedex-card>
        </div>
      </div>
      <div class="row">
        <div class="col-md-12 text-center mt-3">
          <button class="btn btn-primary" @click.prevent="showMorePokemon">Ver más</button>
        </div>
      </div>
    </section>
  </default-layout>
</template>
<script>
import DefaultLayout from '@/layouts/DefaultLayout'
import PokedexCard from '@/components/PokedexCard'
import {getPokemon} from '@/services/pokemon'
export default {
  name: 'HomeView',
  data () {
    return {
      pokemon: [],
      limit: 12,
      filter: ''
    }
  },
  created () {
    getPokemon().then(response => {
      this.pokemon = response.data
    }).catch(err => console.error(err))
  },
  computed: {
    filteredPokemon () {
      let filteredPokemon = (this.filter === '') ? this.pokemon : this.pokemon.filter(item => {
        return item.name === this.filter
      })
      return filteredPokemon.slice(0, this.limit)
    }
  },
  methods: {
    showMorePokemon () {
      this.limit += 12
    }
  },
  components: {
    DefaultLayout,
    PokedexCard
  }
}
</script>
