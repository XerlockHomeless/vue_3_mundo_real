<script setup>
import { ref, onMounted } from 'vue'
import EventCard from '@/components/EventCard.vue'
import axios from 'axios'

const events = ref(null)

onMounted(() => {
  axios
    .get('https://my-json-server.typicode.com/XerlockHomeless/vue_3_mundo_real/events')
    .then(res => {
      events.value = res.data
    })
    .catch(rej => {
      alert(rej)
      console.error(rej)
    })
})
</script>

<template>
  <h1>Events For Good</h1>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<style scoped>
.events{
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>