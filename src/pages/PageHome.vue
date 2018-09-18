<template>
  <div class="col-full">
    <h1>Welcome to the forum maddafacka!</h1>
    <Threadlist :threads="threads"/>
  </div>
</template>

<script>
  import sourceData from '@/data'
  import Threadlist from '../components/ThreadList'
  console.log(sourceData)
  export default {
    data () {
      return {
        threads: Object.values(sourceData.threads),
        posts: sourceData.posts,
        users: sourceData.users
      }
    },

    components: {
      Threadlist
    }
  }
</script>