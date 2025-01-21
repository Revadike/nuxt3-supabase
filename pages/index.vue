<script setup>
const client = useSupabaseClient()
const user = useSupabaseUser()

const logout = async () => {
  await client.auth.signOut()
}
</script>

<template>
  <div v-if="user">
    <p>
      You are logged in as {{ user.email }}.
    </p>
    <button @click="logout">
      Log out
    </button>
  </div>
  <div v-else>
    <p>
      You are not logged in.
    </p>
  </div>
</template>
