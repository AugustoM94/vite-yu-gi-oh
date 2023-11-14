<template>
  <div>
    <HeaderApp />
    <div class="bg-main">
      <main class="container p-5">
        <SearchBar
          :archetypeList="archetypeList"
          @eventArchetypeChange="archetypeUpdate"
        />
        <CharacterList :characters="filteredCharacters" class="bg-white" />
        <LoaderComponent v-if="store.loading" />
      </main>
    </div>
  </div>
</template>

<script>
import { store } from './data/store.js';
import axios from 'axios';
import HeaderApp from './components/HeaderApp.vue'
import CharacterList from './components/CharacterList.vue';
import SearchBar from './components/SearchBar.vue';
import LoaderComponent from './components/LoaderComponent.vue';

export default {
  name: 'App',
  components: {
    HeaderApp,
    CharacterList,
    LoaderComponent,
    SearchBar,
  },
  data() {
    return {
      store,
      archetypeList: [],
      filteredCharacters: [],
      selectedArchetype: null,
    };
  },
  methods: {
    getCharacters() {
      const url = store.apiUrl + store.endPoint.character;
      const params = {
        archetype: this.selectedArchetype,
      };

      axios.get(url, { params }).then((response) => {
        store.characterList = response.data.data;
        this.filteredCharacters = [...response.data.data];
      });

      axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php').then((response) => {
        this.archetypeList = response.data;
      });
    },
    archetypeUpdate(archetype) {
      this.selectedArchetype = archetype;
      this.getCharacters();
    },
    searchByName(name) {
      this.filteredCharacters = this.store.characterList.filter((character) =>
        character.name.toLowerCase().includes(name.toLowerCase())
      );
    },
  },
  created() {
    this.getCharacters();
  },
};
</script>

<style lang="scss" scoped>
.bg-main {
  background-color: #D48F38;
}
section {
  padding: 60px;
}
</style>
