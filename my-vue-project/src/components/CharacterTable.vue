<template>
  <table>
    <thead>
      <tr>
        <th>Name</th>
        <th>Strength</th>
        <th>Speed</th>
        <th>Skill</th>
        <th>Fear Factor</th>
        <th>Power</th>
        <th>Intelligence</th>
        <th>Wealth</th>
        <th>Selected</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="character in characters" :key="character.id">
        <td>{{ character.name }}</td>
        <td>{{ character.strength }}</td>
        <td>{{ character.speed }}</td>
        <td>{{ character.skill }}</td>
        <td>{{ character.fear_factor }}</td>
        <td>{{ character.power }}</td>
        <td>{{ character.intelligence }}</td>
        <td>{{ character.wealth }}</td>
        <td>
            <input type="checkbox"
                            :value="character"
                            :checked="isSelected(character)"
                            @change="toggleSelection(character)">        
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      characters: [],
      selectedCharacters: [],
      loading: false,
      error: null
    };
  },
  methods: {
    fetchCharacters() {
      this.loading = true;
      axios.get('http://localhost:3000/api/characters')
        .then(response => {
            console.log(response.data);
          this.characters = response.data;
        })
        .catch(error => {
          this.error = 'Failed to load characters: ' + error.message;
        })
        .finally(() => {
          this.loading = false;
        });
    },
    toggleSelection(character) {
      const index = this.selectedCharacters.findIndex(c => c.id === character.id);
      if (index !== -1) {
        this.selectedCharacters.splice(index, 1); // Remove from selection
      } else {
        this.selectedCharacters.push(character); // Add to selection
      }
    },
    isSelected(character) {
      return this.selectedCharacters.some(c => c.id === character.id);
    }
  },
  mounted() {
    this.fetchCharacters();
  }
};
</script>

<style>
.error {
  color: red;
}
</style>