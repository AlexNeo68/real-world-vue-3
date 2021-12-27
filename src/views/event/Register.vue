<template>
  <div v-if="event">
    <h1>Register</h1>
    <button @click="register">Register</button>
  </div>
</template>
<script>
export default {
  props: ['event'],
  inject: ['GStore'],
  methods: {
    register() {
      this.GStore.flashMessage = 'Your success register to the event!'
      setTimeout(() => {
        this.GStore.flashMessage = ''
      }, 2000)
      this.$router.push({ name: 'EventDetails' })
    },
  },
}
</script>