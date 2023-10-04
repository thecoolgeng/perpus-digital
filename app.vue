<template>
  <div>
    <NuxtWelcome />
  </div>
</template>

<script setup>
const client= useSupabaseClient()
console.log(client)
</script>
