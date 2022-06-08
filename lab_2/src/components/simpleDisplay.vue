<template>
   <ol class="default" ref="simpleDisplayList">
     <li v-for="(item, index) in list" v-bind:key="index">
      {{ item }}
    </li>
   </ol>
</template>

<script>
export default {
  name: 'simpleDisplay',
  props: {
    list: Array,
  },
  mounted() {
    if (this.$refs.simpleDisplayList.classList.length > 1) {
      this.$refs.simpleDisplayList.classList.remove('default')
    }
  },
}
</script>

<style>
.default {
  color: red;
}
</style>