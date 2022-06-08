<template>
  <div class="flexColumnDiv">
    <label for="dropdownBreeds">Select You breeds</label>
    <select id="dropdownBreeds" v-model="selected" @change="selectedEvent" multiple size=20>
      <option v-for="(option, index) in data" :value="option" v-bind:key="index"> {{ option }} </option>
    </select>
  </div>
</template>

<script>
export default {
  name: 'simpleSelect',
  props: {
    data: Array,
  },
  data() {
    return {
      selected: [],
    }
  },
  methods: {
    selectedEvent() {
      this.$emit('selectedEvent', this.selected)
    },
  }
}
</script>

<style>
option {
  font-size: 16px;
}

.flexColumnDiv {
  display: flex;
  flex-direction: column;
}
</style>