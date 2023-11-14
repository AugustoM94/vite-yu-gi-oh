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
      const characterUrl = store.apiUrl + store.endPoint.character;
      const archetypeUrl = 'https://db.ygoprodeck.com/api/v7/archetypes.php';

      Promise.all([
        axios.get(characterUrl, { params: { archetype: this.selectedArchetype } }),
        axios.get(archetypeUrl)
      ])
        .then((responses) => {
          const charactersResponse = responses[0];
          const archetypesResponse = responses[1];

          store.characterList = charactersResponse.data.data;
          this.filteredCharacters = [...charactersResponse.data.data];
          this.archetypeList = archetypesResponse.data;
        })
        .catch((error) => {
          console.error('Error fetching data:', error);
        });
    },
    archetypeUpdate(archetype) {
      this.selectedArchetype = archetype;
      this.getCharacters();
    },
  },
  created() {
    this.getCharacters();
  },
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
