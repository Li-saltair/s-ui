<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <div style="background:#000;padding:20px;">
    <Button type="primary" loading>Hello！</Button>
    <Button type="danger" icon="error" size="large">Hello！</Button>
    <Button type="default" icon="download" size="small">Hello！</Button>
    <Button type="dashed" icon="hand">Hello！</Button>
  </div>
  <Icon icon="huangguan" color="#C75872"/>
  <HelloWorld msg="Welcome to Your Vue.js App"/>
</template>

<script>
import Icon from './components/icon.vue'
import Button from './components/button/button.vue'
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,Icon,Button
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
