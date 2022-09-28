<template>
  <div id="app">
    <img src="https://sun9-14.userapi.com/impf/c824202/v824202436/117a84/BvhM8SHRHjc.jpg?size=801x785&quality=96&sign=7f0d4b1971668adb30ab80a12b25d0b2&type=album" width="150">
    <HelloWorld msg="Welcome to wordchanger App"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
