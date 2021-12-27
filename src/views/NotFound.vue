<template>
  <div>
    <h1> This page is not found!</h1>
    <p></p>
    <p>Go <router-link :to="{name: 'EventList'}">Home</router-link>
    </p>
  </div>
</template>
<script>
export default {
  props: {
    resource: {
      type: String,
      required: false,
      default: 'page',
    },
  },
}
</script>