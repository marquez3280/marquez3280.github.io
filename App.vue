<template>
  <div id="app">
    <HeaderComponent />
    <router-view />
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue'

export default {
  components: {
    HeaderComponent
  }
}
</script>

<style>
body {
  margin: 0;
  font-family: 'Poppins', sans-serif;
  background: #f4ffe6;
}
</style>
