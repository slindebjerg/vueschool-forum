<template>
  <div>
    <h1>Page not found</h1>
    <p>Look's like youve gone astray. <router-link :to="{name: 'Home'}">Want to go home?</router-link></p>
  </div>
</template>

<script>
  
</script>

<style scoped>
  h1{
    font-size: 100px;
  }

  p{
    font-size: 50px;
  }

  div{
    font-weight: 100;
    text-align: center;
  }
</style>
