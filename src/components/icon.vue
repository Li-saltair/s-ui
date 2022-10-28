<template>
  <svg class="s-icon" aria-hidden="true" :style="{fontSize:`${size}px`,color:`${color}`}">
    <use :xlink:href="`#i-${icon}`"></use>
</svg>
</template>
<script setup>
import { defineProps } from "vue";
import '@/assets/iconfont.js'

const props = defineProps({
  icon:{
    type:String,
    required:true
  },
  size:{
    type:Number,
    required:false,
    default:20
  },
  color:{
    type:String,
    required:false,
    default:'#C75872'
  }
})
</script>
<style lang="less">
  .s-icon {
      width: 1em; height: 1em;
      vertical-align: -0.15em;
      fill: currentColor;
      overflow: hidden;
  }
</style>