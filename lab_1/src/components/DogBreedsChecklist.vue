<template>
<div>
  <h3>Get random breed</h3>
  <input type="button" @click="insertRandomBreed()" value="Insert Random">
  <input type="button" @click="deleteRandomBreed()" value="Delete Random">
  <input type="button" @click="shuffleArray()" value="Shuffle Array">
  <pre>
    {{chosenBreeds}}
  </pre>
</div>
</template>

<script>
export default {
  name: 'DogBreedsChecklist',
  props: {
    sourceURL: String
  },
  data() {
    return {
      chosenBreeds: Array(),
      getAllBreedURL: this.sourceURL + "/breeds/list/all",
    }
  },
  methods: {
    insertRandom(breeds){
      let breedCandidats = [];
      Object.keys(breeds).forEach(breed => {
        if (!this.chosenBreeds.includes(breed)){
          breedCandidats.push(breed);
        }
      })
      if (breedCandidats.length > 0){
        this.chosenBreeds.push(breedCandidats[Math.floor(Math.random()*breedCandidats.length)]);
      } else {
        alert('Sorry, but no new breed was added as all breeds are in the list')
      }
    },
    insertRandomBreed() {
      fetch(this.getAllBreedURL)
        .then(response => response.json())
        .then((data) => this.insertRandom(data.message));
    },
    deleteRandomBreed(){
      this.chosenBreeds.splice([Math.floor(Math.random()*this.chosenBreeds.length)], 1);
    },
    shuffleArray() {
      for (let i = this.chosenBreeds.length - 1; i > 0; i--) {
        let j = Math.floor(Math.random() * (i + 1));
        [this.chosenBreeds[i], this.chosenBreeds[j]] = [this.chosenBreeds[j], this.chosenBreeds[i]];
      }
      this.$forceUpdate();
    }
  }
}
</script>