<template>
  <div id="q-app">
    <router-view />
  </div>
</template>
<script>
export default {
  name: 'App'
}
</script>
<style>
  body::-webkit-scrollbar {
     width: 10px
} 
   
body::-webkit-scrollbar-thumb {   
background-color: #bf830091   
}

</style>