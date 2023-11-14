<template>
  <div class="app-searchbar">
    <select class="me-2" name="card-archetype" id="card-archetype" @change="handleArchetypeChange">
      <option selected hidden>Choose an Archetype</option>
      <option v-for="archetype in archetypeList" :key="archetype.id">
        {{ archetype.archetype_name }}
      </option>
    </select>
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
    handleArchetypeChange(event) {
      this.$emit('eventArchetypeChange', event.target.value);
    },
  },
};
</script>

<style lang="scss" scoped>
.app-searchbar {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  width: 80%;
  margin: 0 auto;
  padding: 1rem;
}
select{
  width: 250px;
  padding: 10px;
  border-radius: 10px;
  background-color: rgba($color: #ffffff, $alpha: 0.4);
}
</style>
