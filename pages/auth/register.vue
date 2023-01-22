<template>
  <form class="row flex-center flex" @submit.prevent="handleRegister">
    <div class="col-6 form-widget">
      <h1 class="header">Projex Register</h1>
      <p class="description">Email and Password</p>
      <div>
        <input class="inputField" type="email" placeholder="Your email" v-model="email" />
      </div>
      <div>
        <input class="inputField" type="password" placeholder="Your password" v-model="password" />
      </div>
      <div>
        <input
            type="submit"
            class="button block"
            :value="loading ? 'Loading' : 'Kaydet'"
            :disabled="loading"
        />
      </div>
    </div>
  </form>
</template>

<script setup lang="ts">
const client = useSupabaseClient()

const loading = ref(false)
const email = ref('')
const password = ref('')
const handleRegister = async () => {
  console.log(email)
  const { data, error } = await client.auth.signUp(
      {
        email: email.value,
        password: password.value,
        options: {
          data: {
            lisans: '202302'
          }
        }
      }
  )
  console.log(data)
  console.log(error)
}



</script>