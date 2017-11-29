<script>
export default {
  name: 'PokedexTag',
  props: {
    pokemonType: {
      type: String,
      required: true
    }
  },
  render (h) {
    return <span class="pokedex-tag badge badge-primary mr-1">
      {this.pokemonType}
    </span>
  }
}
</script>
