<template lang="html">
  <div v-if="character" id="characterDetail">
    <div id="detailWrapper">
      <h2>{{character.name}}</h2>
      <div id="flexWrapper">
        <div id="left">
          <p><span>Name</span>: {{character.name}}</p>
          <p><span>Birthday</span>: {{character.birthday}}</p>
          <p><span>Occupation</span>: {{character.occupation}}</p>
          <p><span>Status</span>: {{character.status}}</p>
          <p><span>Seasons</span>: {{character.appearance}}</p>
          <p><span>Nickname</span>: {{character.nickname}}</p>
          <p><span>Portrayed By</span>: {{character.portrayed}}</p>
          

        </div>
        <div id="right">
          <img :src="character.img" :alt="character.img">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { eventBus } from '../main.js'
export default {
  name: 'character-detail',
  data(){
    return {
      character: null
    }
  },
  mounted(){
    eventBus.$on('character-selected', (character) => {
      this.character = character
    })
  }
}
</script>

<style lang="css" scoped>
  #characterDetail {
    box-sizing: border-box;
    height: 400px;
    width: 60%;
    background: #eee;
    padding: 10px;
    border: 1px solid #ccc;
    margin: 0 auto;
  }
  #characterWrapper {
    box-sizing: border-box;
    background: #fff;
    padding: 10px;
    height: 100%;
    border-radius: 3px;
  }
  #flexWrapper {
    display: flex;
    justify-content: space-between;
  }
  #left, #right {
    width: 45%;
  }
  #right img {
    width: 100%;
  }
  #left p:first-child {
    margin-top: 0;
  }
  h2 {
    margin: 10px 0 20px;
    padding: 0;
  }
  p span {
    font-weight: bold;
  }
</style>