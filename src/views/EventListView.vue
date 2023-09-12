<script setup>
import EventCard from '@/components/EventCard.vue'
import { onMounted, ref } from 'vue'
import axios from 'axios'
import EventService from '@/services/EventService'

const events = ref([])

onMounted(() => {
  EventService.getEvents()
    .then((res) => (events.value = res.data))
    .catch((err) => console.error(err))
})
</script>

<template>
  <h1>Events for Good</h1>
  <div class="events">
    <event-card
      v-for="event in events"
      :event="event"
      :key="event.id"
    ></event-card>
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
