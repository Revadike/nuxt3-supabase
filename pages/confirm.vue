<script setup>
const user = useSupabaseUser()
const supabase = useSupabaseClient()

const params = new URLSearchParams(window.location.search)

const {
  data: { session },
  error,
} = await supabase.auth.verifyOtp({
  token_hash: params.get('token'),
  type: 'email',
})

console.log({ token, email, error, session })

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
    </p>
  </div>
</template>
