<template>
  <div v-if="event">
    <h1>{{event.title}}</h1>
    <p>@{{event.date}} at {{event.time}} on {{event.location}}</p>
    <p>{{event.description}}</p>

  </div>
</template>
<script>
export default {
  props: ['event'],
}
</script>