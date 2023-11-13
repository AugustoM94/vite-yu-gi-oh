<template>
      <HeaderApp/>
   <div class="bg-main">
        <main class="container">
    <MainApp/>
      </main>
      </div>
    <CharacterList />
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
      axios.get(url).then((response) => {
        store.characterList = response.data.results;
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
    height: 100vh;
}
</style>