<template>
  <h1>Projex</h1>
  <NuxtLink to="/auth/login">Login</NuxtLink> - <button class="button" @click="handleLogout">Logout</button>
  <div>
    <h1>Welcome to the sdfsfs</h1>
    <div v-for="(item, index) in data" :key="`item${index}`">
      <span>{{ item.unvan }}</span>
    </div>
  </div>
</template>

<script setup lang="ts">
const client = useSupabaseClient()
const router = useRouter()

const { data: { user } } = await client.auth.getUser()

console.log(user)
if (!user) router.push('/auth/login')

const handleLogout = async () => {

  const { error } = await client.auth.signOut()
  console.log(error)
  if (error) throw error
  router.push('/auth/login')
}
const { data, error } = await client
    .from('customers')
    .select('*')
</script>