<template>
  <form @submit.prevent="onSearch">
    <input v-model="searchQuery" type="text" placeholder="Search for characters">
  </form>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: ''
    };
  },
  methods: {
    onSearch() {
      this.$emit('search', this.searchQuery);
    }
  }
};
</script>
