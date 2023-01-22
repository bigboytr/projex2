<template>
  <form @submit.prevent="handleLogin">
    <div class="flex flex-col border border-black p-3 gap-y-4">
      <h1>Projex Login</h1>
      <Input :type="'email'" :placeholder="'Email adres'" />
      <Input :type="'password'" :placeholder="'Şifreniz'" />
      <Button submit :class-name="'warn'">Giriş</Button>
    </div>
  </form>
</template>

<script setup lang="ts">
const client = useSupabaseClient()
const router = useRouter()

const loading = ref(false)
const email = ref('')
const password = ref('')
const handleLogin = async () => {
  try {
    await client.auth.updateUser({password: '123456'})
    loading.value = true
    const {error} = await client.auth.signInWithPassword({email: email.value, password: password.value})
    if (error) throw error
    router.push('/')
  } catch (error) {
    alert(error.error_description || error.message)
  } finally {
    loading.value = false
  }
}
</script>