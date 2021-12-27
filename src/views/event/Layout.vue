<template>
  <div v-if="event">

    <ul class="navigation">
      <li>
        <router-link :to="{name: 'EventDetails'}">Details</router-link>
      </li>
      <li>
        <router-link :to="{name: 'EventRegister'}">Register</router-link>
      </li>
      <li>
        <router-link :to="{name: 'EventEdit'}">Edit</router-link>
      </li>

    </ul>
    <router-view :event="event"></router-view>

  </div>
</template>
<script>
import EventService from '@/services/EventService.js'
export default {
  props: ['id'],
  data() {
    return {
      event: null,
    }
  },
  created() {
    EventService.getEvent(this.id)
      .then((res) => (this.event = res.data))
      .catch((err) => {
        if (err.status && err.status == 404) {
          this.$router.push({
            name: '404Resource',
            params: { resource: 'event' },
          })
        }
      })
  },
}
</script>