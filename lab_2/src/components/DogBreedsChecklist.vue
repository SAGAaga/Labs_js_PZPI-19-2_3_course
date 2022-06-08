<template>
<div>
  <h3>Lab 2 Sahaidachnyi Nikita</h3>
  <div class="flexDiv" style="justify-content: space-between;">
    <div class="flexDiv">
      <simpleSelect :data="breeds" @selectedEvent="simpleSelectedEvent"></simpleSelect>
      <simpleDisplay :list="selectedBreeds"></simpleDisplay>
    </div>
    <div class="flexDiv">
      <castomSelect :data="breeds" @selectedEvent="castomSelectedEvent"></castomSelect>
      <simpleDisplay class="blueFont" :list="castomSelectedBreeds"></simpleDisplay>
    </div>
  </div>
</div>
</template>

<script>
import simpleSelect from './simpleSelect.vue'
import castomSelect from './castomSelect.vue'
import simpleDisplay from './simpleDisplay.vue'

export default {
  name: 'DogBreedsChecklist',
  components: {
    simpleSelect,
    simpleDisplay,
    castomSelect
  },
  props: {
    sourceURL: String
  },
  data() {
    return {
      breeds: Array(),
      selectedBreeds: Array(),
      castomSelectedBreeds: Array(),
      getAllBreedURL: this.sourceURL + "/breeds/list/all",
    }
  },
  created() {
    this.fetchBreeds()
  },
  methods: {
    simpleSelectedEvent(data) {
      this.selectedBreeds = data
    },
    castomSelectedEvent(data) {
      this.castomSelectedBreeds = data
    },
    fetchBreeds() {
      fetch(this.getAllBreedURL)
        .then(response => response.json())
        .then((data) => this.breeds = Object.keys(data.message));
    },
  }
}
</script>

<style>
.flexDiv {
  width: 800px;
  display: flex;
}

.blueFont{
  color: blue;
}
</style>