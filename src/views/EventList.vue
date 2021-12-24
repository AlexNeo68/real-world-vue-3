<template>
  <div class="home">
    <h1>Events</h1>
    <div class="events">
      <EventCard
        v-for="event in events"
        :event="event"
        :key="event.id"
      />
    </div>

  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from '@/components/EventCard.vue'

export default {
  name: 'EventList',
  components: {
    EventCard,
  },
  data() {
    return {
      events: null,
    }
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
</style>