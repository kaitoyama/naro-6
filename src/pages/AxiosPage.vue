<script setup>
import axios from "axios";
const sendGet = () => axios.get("https://eozsmjvqdyby44v.m.pipedream.net");
const sendPost = () =>
  axios.post("https://eozsmjvqdyby44v.m.pipedream.net", {
    traQID: "kaitoyama",
    grade: 18,
  });
const sendPut = () =>
  axios.put("https://eozsmjvqdyby44v.m.pipedream.net", {
    testData: { string: "string", number: 1 },
  });
const sendDelete = () =>
  axios.delete("https://eozsmjvqdyby44v.m.pipedream.net", {
    data: { po: 1 },
  });
</script>

<template>
  <div>
    <button @click="sendGet">GET</button>
    <button @click="sendPost">POST</button>
    <button @click="sendPut">PUT</button>
    <button @click="sendDelete">DELETE</button>
  </div>
</template>
