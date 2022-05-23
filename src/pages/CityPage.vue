<script setup>
import axios from "axios";
import router from "../router.js";
import { ref, onMounted } from "vue";
const cityName = ref("");
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

const getInfo = () => {
  router.replace({ name: "city", params: { cityName: cityName.value } });
  setTimeout(() => {
    router.go({ path: router.currentRoute.path, force: true });
  }, 100);
};
</script>

<template>
  <div>
    <h1>{{ props.cityName }}</h1>
  </div>
  <div>
    <p>enter city Name</p>
    <input v-model="cityName" type="text" />
  </div>
  <div>
    <button @click="getInfo">Go!</button>
  </div>
  <div>
    <button @click="update">!!</button>
  </div>
  <div v-if="cityInfo">{{ cityInfo }}</div>
  <div v-else>街が見つかりませんでした</div>
</template>
