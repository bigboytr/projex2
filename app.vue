<template>
  <div>
    <h1>Welcome to the homepage</h1>
    <div v-for="(item, index) in data" :key="`item${index}`">
      <span>{{ item.unvan }}</span>
    </div>
  </div>
</template>

<script setup lang="ts">
const runtimeConfig = useRuntimeConfig()
/*const client = useSupabaseClient()

const { data, error } =  await client.from('customers').select('id, firstname')
console.log(data)
console.log(error)*/



import { createClient } from '@supabase/supabase-js'

// Create a single supabase client for interacting with your database
const supabase = createClient(runtimeConfig.url, runtimeConfig.key)


const { data, error } = await supabase
    .from('customers')
    .select('*')

console.log(data, error)
</script>