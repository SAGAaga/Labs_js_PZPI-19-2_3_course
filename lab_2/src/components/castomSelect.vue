<template>
  <div class="flexColumnDiv">
    <h4>Select You breeds</h4>
    <div style="overflow-y:scroll; max-height: 400px;">
      <div
          class="boxItem" 
          :class="{selected: selected.includes(breed)}"
          v-for="(breed, index) in data" 
          :value="breed" 
          v-bind:key="index"
          @click="clickItemEvent(breed)"
        > 
          {{ breed }} 
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'simpleSelect',
  props: {
    data: [],
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
    clickItemEvent(breed) {
      const index = this.selected.indexOf(breed);
      if (index > -1) {
        this.selected.splice(index, 1);
      } else {
        this.selected.push(breed)
      }
      this.selectedEvent()
    },
  }
}
</script>

<style>
h4 {
  margin-top: 5px;
}

option {
  font-size: 16px;
}

.flexColumnDiv {
  display: flex;
  flex-direction: column;
}

.boxItem {
  margin: 8px 2px;
  font-size: 18px;
  cursor: pointer;
}

.selected {
  background-color: rgb(138, 138, 197);
}
</style>