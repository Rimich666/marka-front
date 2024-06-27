<script setup lang="ts">
  export type TopRowProps = {
    key: number;
    name: string;
    budget: number;
    status: string;
    tutor: string;
    date: Date;
    }
  defineProps<{
    props: TopRowProps;
  }>()
</script>

<template>
  <div class="row">
    <button></button>
    <p  class="cell cell-text">{{props.name}}</p>
    <p class="cell">{{props.budget}}</p>
    <p class="cell cell-text">{{props.status}}</p>
    <p class="cell cell-text">{{props.tutor}}</p>
    <p class="cell">{{props.date}}</p>
  </div>
</template>

<style scoped>
  button {
    width: 10px;
    height: 1px;
  }
</style>