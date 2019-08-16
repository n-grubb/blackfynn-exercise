<template>
  <form class="searchbar">
    <input v-model="search_string" v-on:keyup="filterUsers" type="text" class="search" placeholder="Type user name to filter results" />
    <p class="results"><span class="results-number">{{ results.length }}</span> Results</p>
  </form>
</template>

<script>
export default {
  name: 'SearchBar',
  props: {
    results: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      search_string: ''
    }
  },
  methods: {
    filterUsers() {
      this.$emit('search-user-list', this.search_string);
    }
  }
}
</script>

<style lang="scss">
  .searchbar {
    display: grid;
    grid-template: 2em / 3fr 1fr;
  }

  .search {
    grid-column: 1;
  }

  .results {
    grid-column: 2;
    padding: 0 5px;

    display: flex;
    align-items: center;
    justify-content: center;
  }

  .results-number {
    margin-right: .25em;
  }
</style>
