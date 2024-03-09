<template>
  <div>
    <h1>{{ $route.params.id }}</h1>
  </div>
</template>

<script setup lang="ts">
const { params } = useRoute();
console.log(params.id);
</script>

<style scoped></style>
