<template>
<div>
  <h3>All dog breeds</h3>
  <pre>
    <ol>
      <li v-for="( subBreeds, breed ) in breeds" :key="breed" :class="{highlighteRed: subBreeds.length > 0}">
        {{breed}}: {{subBreeds}}
      </li>
    </ol>
  </pre>
</div>
</template>

<script>
export default {
  name: 'DogBreedsListing',
  props: {
    sourceURL: String
  },
  data() {
    return {
      breeds: {}
    }
  },
  created() {
    // fetch on init
    this.fetchData()
  },
  methods: {
    fetchData() {
      fetch(this.sourceURL + "/breeds/list/all")
        .then(response => response.json())
        .then((data) => this.breeds = data.message);
    },
  }
}
</script>

<style scoped>
.highlighteRed{
  color: red;
}
</style>
