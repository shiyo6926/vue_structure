<template>
    <div id="home">
      <AppHeader />
      <SearchForm @search="handleSearch" />
      <CharacterTable :characters="filteredCharacters" @toggle-select="handleToggleSelect" />
    </div>
  </template>
  
  <script>
  import AppHeader from '@/components/AppHeader.vue';
  import SearchForm from '@/components/SearchForm.vue';
  import CharacterTable from '@/components/CharacterTable.vue';
  
  export default {
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'home',
    components: {
      AppHeader,
      SearchForm,
      CharacterTable
    },
    data() {
      return {
        characters: [],
        filteredCharacters: [],
        searchQuery: ''
      };
    },
    methods: {
      fetchCharacters() {
        this.fetchCharacters().then(data => {
          this.characters = data;
          this.filteredCharacters = data; // Initialize filteredCharacters
        });
      },
      handleSearch(query) {
        this.searchQuery = query;
        this.filteredCharacters = this.characters.filter(character =>
          character.name.toLowerCase().includes(this.searchQuery.toLowerCase())
        );
      },
    },
    mounted() {
      this.fetchCharacters();
    }
  };
  </script>
  
  <style>
  </style>
  