<template>
  <div>
    <h1>Привет {{ userName }}!</h1>
    <input @input="updateUserName" type="text">
  </div>
</template>

<script>
export default {
  name: 'ClientGritting',
  data() {
    return {
      userName: 'незнакомец'
    }
  },
  methods: {
    updateUserName(e) {
      this.userName = e.target.value || 'незнакомец'
    },
  }
}
</script>