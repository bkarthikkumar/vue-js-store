<template>
  <Header/>
  <Products/>
  <Footersection/>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header.vue';
import Footersection from './components/Footer.vue';
import Products from './components/ProductsList.vue';
export default {
  name      : 'App',
  components: {
    // HelloWorld,
    Header,
    Footersection,
    Products,
  }
}
</script>

<style>
#app {
  font-family            : Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing : antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align             : center;
  color                  : #2c3e50;
  margin-top             : 2px;
}
</style>
