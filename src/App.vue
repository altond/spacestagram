<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  methods: {
    async getImages() {
      const response = await axios.get("https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY")
        .catch(err => console.log(err)
        );

      console.log("yeet")
      console.log(response)
    }
  },
  mounted() {
    this.getImages()
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
