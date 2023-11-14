<template>
  <HeaderApp/>
<div class="bg-main">
    <main class="container p-5">
     <SearchBar
            :archetypeList="archetypeList"
            @eventArchetypeChange="archetypeUpdate"
            @eventNameSearch="searchByName"
      /> 
      <CharacterList class="bg-white"/>
      <LoaderComponent v-if="store.loading" />
  </main>
  </div>
</template>

<script>
import { store } from './data/store.js';
import axios from 'axios';
import HeaderApp from './components/HeaderApp.vue';
import CharacterList from './components/CharacterList.vue';
import SearchBar from './components/SearchBar.vue';
import LoaderComponent from './components/LoaderComponent.vue';
export default {
name: 'App',
components: {
      HeaderApp,
      CharacterList,
      LoaderComponent,
      SearchBar
},
data() {
return {
        store,
        archetypeList: [] 
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
          axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php')
            .then(response => {
                console.log(response.data);
                this.archetypeList = [...response.data];
            })
        },
        archetypeUpdate(archetype) {
                axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=' + archetype)
                    .then(function (response) {
                        console.log(response.data.data);
                        store.yugiohApi = response.data.data;
                    })

        },
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