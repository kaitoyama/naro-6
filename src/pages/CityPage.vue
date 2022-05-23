<script setup>
import axios from "axios";
import router from "../router.js";
import { ref, onMounted } from "vue";
const props = defineProps({
  cityName: {
    type: String,
    required: true,
  },
});
const cityName = {
  template: ref(),
  async beforeRouteUpdate(to, from, next) {
    cityName.value = from;
    next();
    cityName.value = to;
  },
};
const cityInfo = ref();
onMounted(async () => {
  const res = await axios.get("/api/cities/" + props.cityName);
  cityInfo.value = res.data;
});
const getInfo = () =>
  router.go({ name: "city", params: { cityName: cityName } });
</script>

<template>
  <div>
    <h1>{{ cityName }}</h1>
    <div>
      <p>enter city Name</p>
      <input v-model="cityName" type="text" />
    </div>
    <div>
      <button @click="getInfo">Go!</button>
    </div>
    <div v-if="cityInfo">{{ cityInfo }}</div>
    <div v-else>街が見つかりませんでした</div>
  </div>
</template>
