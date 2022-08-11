<template>
  <q-list bordered>
    <q-item clickable v-ripple v-for="(news, idx) in newsDatas" :key="news.id">
      <q-item-section>{{ news.title }}</q-item-section>
      <q-item-section side>{{
        dateFormatter(1640120668320 + idx * 1000000)
      }}</q-item-section>
    </q-item>
  </q-list>
</template>

<script setup>
import { onMounted, ref } from "vue";
import axios from "axios";
import moment from "moment";

// ===============================REF===============================
const newsDatas = ref([]);

// ===============================MOUNTED===============================
onMounted(() => {
  axios.get("https://jsonplaceholder.typicode.com/posts").then((res) => {
    console.log(res);
    newsDatas.value = res.data;
  });
});

// ===============================FUNC===============================
const dateFormatter = (date) => {
  return moment(date).fromNow();
};
</script>
