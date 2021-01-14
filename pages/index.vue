
<template>
 <ul>
  <li v-for="content in contents" :key="content.id">
   <nuxt-link :to="`/${content.id}`">
    {{ content.title }}
   </nuxt-link>
  </li>
 </ul>
</template>


<script>
import axios from 'axios'
export default {
 async asyncData(){
  const{ data } = await axios.get(
    'https://t1964101.microcms.io/api/v1/blog',
    {
    headers:{'X-API-KEY':'36847a75-600f-438f-b270-1a08a33fc637'}
    }
  )
  return data
 }
}
</script>


