<script setup lang="ts">
const route = useRoute()
console.log('route',route)
</script>

<template>
<div>
  视频页{{ route.params.id }}
</div>
</template>

<style scoped>
</style>
