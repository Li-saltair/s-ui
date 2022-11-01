<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <div style="background:#000;padding:20px;">
    <Button type="primary" loading>Hello！</Button>
    <Button type="danger" icon="error" size="large">Hello！</Button>
    <Button type="default" icon="download" size="small">Hello！</Button>
    <Button type="dashed" icon="hand">Hello！</Button>
    <!-- @click="toggle" -->
    <Button type="primary" @buttonClick="testHandler">切换dialog</Button>
  </div>
  <Dialog title="标题标题标题" v-model:visible="visible" :maskClosable="false" :width="800">
    <!--<template #footer>
      <div>
        <div>传入的内容</div>
        <Button type="dashed" icon="hand">Hello！</Button>

      </div>
    </template>-->
    <div>是开机卡所以房价可是住房预售的结果</div>
  </Dialog>
  <Icon icon="huangguan" color="#C75872"/>
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
</template>

<script>
import {ref} from 'vue'
import Icon from './components/icon.vue'
import Button from './components/button/button.vue'
import Dialog from './components/dialog/dialog.vue'
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,Icon,Button,Dialog
  },
  setup(){
    const visible = ref(true)
    const toggle = ()=>{
      console.log('点击了')
      visible.value = !visible.value
    }
    const testHandler = ()=>{
      console.log('测试事件')
      visible.value = !visible.value
    }
    //这种语法一定不能忘记return定义的数据和方法
    return {
      visible,toggle,testHandler
    }
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
