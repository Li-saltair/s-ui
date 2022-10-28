<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <Icon icon="huangguan" color="#C75872"/>
  <HelloWorld msg="Welcome to Your Vue.js App"/>
</template>

<script>
import Icon from './components/icon.vue'
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,Icon
  }
}
</script>

<style lang="less">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
