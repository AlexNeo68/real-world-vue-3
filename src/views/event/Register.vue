<template>
  <div v-if="event">
    <h1>Register</h1>
    <button @click="register">Register</button>
  </div>
</template>
<script>
export default {
  props: ['event'],
  methods: {
    register() {
      //Api call
      this.$router.push({ name: 'EventDetails' })
    },
  },
}
</script>