<template>
  <div id="app">
        <transition name="el-fade-in-linear" >

    <img v-show="show" class="transition-box" alt="Vue logo" src="./assets/logo.png">
        </transition>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
        <el-button @click="show = !show">Click Me</el-button>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data: () => ({
      show: true
    })
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat&display=swap');

#app {
font-family: 'Montserrat', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
