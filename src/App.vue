<template>
  <h4>Countries directory</h4>
  <div v-for="country in countries" :key="country.name">
    {{ country.name }}
  </div>
</template>

<script setup>
import { onBeforeMount, ref } from 'vue'
import axios from 'axios'
const countries = ref([])

onBeforeMount(() => {
  axios.get('https://restcountries.eu/rest/v2/all').then(res => {
    countries.value = res.data
  })
})
</script>

