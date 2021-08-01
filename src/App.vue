<template>
  <h4>Countries directory</h4>
  <p v-if="loading">Loading...</p>
  <div v-else>
    <ul v-for="country in countries" :key="country.name">
      <li>{{ country.name }}</li>
    </ul>
  </div>
</template>

<script setup>
import { onBeforeMount, ref } from 'vue'
import axios from 'axios'
const loading = ref(true)
const countries = ref([])

onBeforeMount(() => {
  axios.get('https://restcountries.eu/rest/v2/all').then(res => {
    if(countries.value = res.data)
      loading.value = false
  })
})
</script>

