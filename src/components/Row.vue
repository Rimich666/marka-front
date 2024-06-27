<script setup lang="ts">

  import TopRow, {TopRowProps} from "./TopRow.vue";
  import SubRow from "./SubRow.vue";

  defineProps<{
    top: TopRowProps;
  }>()
</script>

<template>
  <TopRow :props=top></TopRow>
<!--  <SubRow/>-->
</template>

<style scoped>

</style>