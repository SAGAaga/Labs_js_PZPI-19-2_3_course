<template>
  <div id="app">
    <div style="display: flex; justify-content: space-around;">
      <DogBreedsChecklist :sourceURL="dogAPI" />
    </div>
  </div>
</template>

<script>
import DogBreedsChecklist from './components/DogBreedsChecklist.vue'

const dogAPI = 'https://dog.ceo/api'

export default {
  name: 'App',
  components: {
    DogBreedsChecklist,
  },
  data() {
    return {
      dogAPI: dogAPI
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
