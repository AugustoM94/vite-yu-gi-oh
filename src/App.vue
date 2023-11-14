<template>
  <HeaderApp/>
<div class="bg-main">
    <main class="container p-5">
      <CharacterList class="bg-white"/>
  </main>
  </div>
</template>

<script>
import { store } from './data/store.js';
import axios from 'axios';
import HeaderApp from './components/HeaderApp.vue';
import CharacterList from './components/CharacterList.vue';
export default {
name: 'App',
components: {
      HeaderApp,
      CharacterList
},
data() {
return {
  store
}
},
methods: {
getCharacters() {
  const url = store.apiUrl + store.endPoint.character;
  console.log(url)
  axios.get(url).then((response) => {
    console.log(response.data.data)
    store.characterList = response.data.data;
  })
}
},
created() {
this.getCharacters();
}
}
</script>

<style lang="scss" scoped>
.bg-main {
background-color: #D48F38;
}
section {
  padding: 60px;
}
</style>