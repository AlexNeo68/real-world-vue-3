<template>
  <div class="home">
    <h1>Events</h1>
    <div class="events">
      <EventCard
        v-for="event in events"
        :event="event"
        :key="event.id"
      />
      <div class="pagination">
        <router-link
          v-if="page!=1"
          :to="{name: 'EventList', query: {page: page - 1}}"
        >Prev</router-link>
        <router-link
          v-if="isNextPage"
          :to="{name: 'EventList', query: {page: page + 1}}"
        >Next</router-link>
      </div>
    </div>

  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from '@/components/EventCard.vue'
import EventService from '@/services/EventService.js'
import { watchEffect } from 'vue'
export default {
  name: 'EventList',
  components: {
    EventCard,
  },
  props: ['page'],
  data() {
    return {
      events: null,
      totalEvents: 0,
    }
  },
  computed: {
    isNextPage() {
      return this.page * 2 < this.totalEvents
    },
  },
  created() {
    watchEffect(() => {
      EventService.getEvents(2, this.page)
        .then((res) => {
          this.events = res.data
          this.totalEvents = res.headers['x-total-count']
        })
        .catch(() => {
          this.$router.push({ name: 'NetworkError' })
        })
    })
  },
}
</script>
<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
  row-gap: 18px;
}
.pagination {
  display: flex;
  justify-content: space-between;
  width: 250px;
}
</style>