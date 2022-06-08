<template>
<div>
  <h3>Get random breed</h3>
  <input type="button" @click="getRandomBreed()" value="GET">
  <pre v-if="randomBreed">
    {{randomBreed['breed']}}: {{randomBreed['subBreeds']}}
  </pre>
</div>
</template>

<script>
export default {
  name: 'DogBreedsRandom',
  props: {
    sourceURL: String
  },
  data() {
    return {
      randomBreed: null,
      getAllBreedURL: this.sourceURL + "/breeds/list/all",
    }
  },
  methods: {
    ChooseRandom(breeds){
      let breedWithSubBreeds = [];
      Object.entries(breeds).forEach(([breed, subBreeds]) => {
        if (subBreeds.length > 0){
          breedWithSubBreeds.push({'breed': breed, 'subBreeds': subBreeds})
        }
      })
      this.randomBreed = breedWithSubBreeds.length > 0 ? breedWithSubBreeds[Math.floor(Math.random()*breedWithSubBreeds.length)] : null 
    },
    getRandomBreed() {
      fetch(this.getAllBreedURL)
        .then(response => response.json())
        .then((data) => this.ChooseRandom(data.message));
    },
  }
}
</script>

<!-- 
<script>
export default {
  name: 'DogBreedsRandom',
  props: {
    sourceURL: String
  },
  data() {
    return {
      randomBreed: null,
      randomSubBreeds: [],
      getRandomBreedURL: this.sourceURL + "/breeds/list/random",
    }
  },
  methods: {
    getRandomBreed() {
      let c = 0;
      while (!(this.randomSubBreeds.length > 0 || c > 60)){
        fetch(this.getRandomBreedURL)
          .then(response => response.json())
          .then((data) => this.randomBreed = data.message);

        setTimeout(() => {}, 1000)
        fetch(this.sourceURL + "/breed/" + this.randomBreed + "/list")
        .then(response => response.json())
        .then((data) => this.randomSubBreeds = data.message);

        c++;
        setTimeout(() => {}, 1000)
      }
    },
  }
}
</script> -->
