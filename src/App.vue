<template>
  <h4>Countries directory</h4>
  <p v-if="loading">Loading...</p>
  <div v-else>
    <input type="text" name="search" placeholder="Type to search..." @input="search" />
    <countries-list :countries="searchCountries.length ?  searchCountries : countries" />
  </div>
</template>

<script setup>
import CountriesList from './components/CountriesList.vue'
import { computed, onBeforeMount, ref } from 'vue'
import axios from 'axios'
const loading = ref(true)
const countries = ref([])
const searchCountries = ref([])
const search = (e) => {
  searchCountries.value = countries.value.filter(item => item.name.toLowerCase().indexOf(e.target.value.toLowerCase()) !== -1);

}

onBeforeMount(() => {
  axios.get('https://restcountries.eu/rest/v2/all').then(res => {
    if(countries.value = res.data)
      loading.value = false
  })
})
</script>

