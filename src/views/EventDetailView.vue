<script setup>
import { onMounted, ref } from 'vue'
import EventService from '@/services/EventService'

const props = defineProps({
  id: {
    required: true,
  },
})
const event = ref()
onMounted(() =>
  EventService.getEventById(props.id)
    .then((res) => (event.value = res.data))
    .catch((err) => console.error(err))
)
</script>

<template>
  <div v-if="event">
    <h1>{{event.title}}</h1>
    <p>{{ event.time }} on {{ event.date }} @{{ event.location }}</p>
    <p>{{event.description}}</p>
  </div>
</template>

<style scoped></style>
