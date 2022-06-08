<template>
  <div id="app">
    <ClientGritting/>
    <div style="display: flex; justify-content: space-around;;">
      <DogBreedsListing :sourceURL="dogAPI" />
      <DogBreedsRandom :sourceURL="dogAPI" />
      <DogBreedsChecklist :sourceURL="dogAPI" />
    </div>
  </div>
</template>

<script>
import ClientGritting from './components/ClientGritting.vue'
import DogBreedsListing from './components/DogBreedsListing.vue'
import DogBreedsRandom from './components/DogBreedsRandom.vue'
import DogBreedsChecklist from './components/DogBreedsChecklist.vue'

const dogAPI = 'https://dog.ceo/api'

export default {
  name: 'App',
  components: {
    ClientGritting,
    DogBreedsListing,
    DogBreedsRandom,
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
pre{
  box-sizing: border-box;
  overflow: auto;
  padding: 9.5px;
  margin: 25px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #333;
  word-wrap: break-word;
  background-color: #f5f5f5;
  border: 1px solid #ccc;
  border-radius: 4px;
  word-break: break-all;
  width: 100%;
  max-height: 400px;
}
</style>
