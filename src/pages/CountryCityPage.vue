<script setup>
import axios from "axios";
import { ref, onMounted } from "vue";
const props = defineProps({
  countryCode: {
    type: String,
    required: true,
  },
});
const cityInfo = ref();
onMounted(async () => {
  const res = await axios.get("/api/country/" + props.countryCode);
  cityInfo.value = res.data;
});
</script>

<template>
  <div>
    <h1>City List</h1>
  </div>
  <li v-for="city in cityInfo" :key="city.name">
    <router-link :to="`/country/${props.countryCode}/${city.name.String}`">
      {{ city.name.String }}</router-link
    >
  </li>
</template>
