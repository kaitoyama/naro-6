<script setup>
import axios from "axios";
import { ref, onMounted } from "vue";
const props = defineProps({
  cityName: {
    type: String,
    required: true,
  },
});
const cityInfo = ref();
onMounted(async () => {
  const res = await axios.get("/api/cities/" + props.cityName);
  cityInfo.value = res.data;
});
</script>

<template>
  <div>
    <h1>{{ props.cityName }}</h1>
  </div>
  <div>
    <li>Name:{{ cityInfo.name.String }}</li>
    <li>Population:{{ cityInfo.population.Int64 }}</li>
  </div>
</template>
