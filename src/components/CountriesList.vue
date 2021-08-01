<template>
  <ul v-for="country in countries" :key="country.name">
    <li>{{ country.name }}</li>
  </ul>
</template>

<script>
export default {
  props: {
    countries: Array
  }
}
</script>
