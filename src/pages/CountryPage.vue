<script setup>
import axios from "axios";
import { ref, onMounted } from "vue";
const countryInfo = ref("");
onMounted(async () => {
  const res = await axios.get("/api/country");
  countryInfo.value = res.data;
});
</script>

<template>
  <div>
    <h1>Country List</h1>
  </div>
  <li v-for="country in countryInfo" :key="country.name.String">
    <router-link :to="`/country/${country.code.String}`">
      {{ country.name.String }}</router-link
    >
  </li>
</template>
