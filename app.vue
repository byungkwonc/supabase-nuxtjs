<script setup>
import { createClient } from '@supabase/supabase-js'
//const supabaseUrl = process.env.SUPABASE_URL
//const supabaseKey = process.env.SUPABASE_ANON_KEY
//const supabase = createClient(supabaseUrl, supabaseKey)
const supabase = createClient('https://vkjafbffelumwqygzzbb.supabase.co', 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InZramFmYmZmZWx1bXdxeWd6emJiIiwicm9sZSI6ImFub24iLCJpYXQiOjE2OTI4Njk3MDMsImV4cCI6MjAwODQ0NTcwM30.2y-Od53iNHzWEuIYtj8QdEyvmQAxXiFl3ltnr0YZ6Vw')
const countries = ref([])

async function getCountries() {
  const { data } = await supabase.from('countries').select()
  countries.value = data
}

onMounted(() => {
  getCountries()
})
</script>

<template>
  <ul>
    <li v-for="country in countries" :key="country.id">{{ country.name }}</li>
  </ul>
</template>