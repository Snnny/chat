<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style lang="scss">
body, html {
  width: 100%;
  height: 100%;
  overflow-y: hidden; 
  #app {
    height: 100%;
  }
}
</style>
