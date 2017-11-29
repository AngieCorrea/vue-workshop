<template>
  <div class="pokedex-card">
    <img class="pokedex-card-img" :src="pokemon.ThumbnailImage"/>
    <div class="pokedex-card-details">
      <small class="pokedex-card-details__number">#{{pokemon.id}}</small>
      <h4 class="pokedex-card-details__title">{{pokemon.name}}</h4>
      <div class="pokedex-card__types">
        <span
          class="badge badge-primary mr-1"
          v-for="(type, index) in pokemon.type"
          :key="index">{{type}}</span>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'PokedexCard',
  props: {
    pokemon: {
      type: Object,
      required: true
    }
  }
}
</script>
