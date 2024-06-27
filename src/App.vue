<script setup lang="ts">
  import axios from 'axios';
  import Head from "./components/Head.vue";
  import Row from "./components/Row.vue";
  import {ref, watchEffect} from "vue";
  import {TopRowProps} from "./components/TopRow.vue";

  type RawData = {
    name: string;
    id: number;
    tutorName: string;
    tutorId: number;
    statusID: number;
    pipeline: number;
    statusName: string;
    budget: number;
    date: Date;
    color: string;
  }

  const leads = ref(null as unknown as TopRowProps[]);

  async function adaptLeans(data: RawData[]): Promise<TopRowProps[]> {
    return data.map((item: RawData) => ({
      name: item.name,
      key: item.id,
      budget: item.budget,
      status: item.statusName,
      tutor: item.tutorName,
      date: item.date,
    }))
  }

  watchEffect(async () => {
    leads.value = await getData();
  })
  async function getData() {
    const {data} = await axios.get('http://localhost:3000/api/leads');
    return adaptLeans(data);
  }

</script>

<template>
  <Head/>
  <Row
    v-for="(item) in leads"
    :top="item"
    :key="item.key"
/>

</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
