<template>
    <div class="app-searchbar">
      <select class=" me-2"
        name="card-archetype" id="card-archetype"  @change="$emit('eventArchetypeChange', $event.target.value)" >
        <option selected hidden>Choose an Archetype</option>
        <option v-for="archetype in archetypeList" :key="archetype.id">
          {{ archetype.archetype_name }}
        </option>
      </select>
      <div class="card-name-search">
        <button class="px-1" @click="eventNameSearch"> Search </button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'SearchBar',
  
    props: {
      archetypeList: Array,
    },
    data() {
      return {
        nameToSearch: '',
      };
    },
    methods: {
      eventNameSearch() {
        if (this.nameToSearch.trim() !== '') {
          this.$emit('eventNameSearch', this.nameToSearch);
          this.nameToSearch = '';
        }
      },
    },
  };
  </script>
  

<style lang="scss" scoped>
div.app-searchbar {
         display: flex;
         justify-content: flex-end;
         align-items: center;
         width: 80%;
         margin: 0 auto;
         padding: 1rem;

}
</style>