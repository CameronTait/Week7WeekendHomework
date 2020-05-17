<template lang="html">
  <div>
    <h1>Characters</h1>
    <character-filter-form :characters="characters" />
    <character-detail />
  </div>
</template>

<script>
import CharacterFilterForm from './components/CharacterFilterForm.vue'
import CharacterDetail from './components/CharacterDetail.vue'
export default {
  data(){
    return {
      characters: [],
    }
  },
  components: {
    "character-filter-form": CharacterFilterForm,
    "character-detail": CharacterDetail
  },
  mounted(){
    fetch('https://breakingbadapi.com/api/characters')
    .then(res => res.json())
    .then(characters => this.characters = characters)
  }
}
</script>

<style lang="css" scoped>
h1 {
  text-align: center;
  color: red;
}

</style>