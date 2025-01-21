<script setup>
const user = useSupabaseUser()

watch(user, () => {
  if (user.value) {
    return navigateTo('/')
  }
}, { immediate: true })
</script>

<template>
  <div>
    <p>
      Redirecting...
      {{ user }}
    </p>
  </div>
</template>
