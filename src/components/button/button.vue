<template>
<!-- @click="click" -->
  <div class="s-button" @click="click">
    <div class="s-button-content" :class="`s-button-${type} s-button-content-${size}`" :style="{borderRadius:`${sharp ? (sharp.toLowerCase() === 'circle' ?  '4px' : 0) : '4px'}`}">
      <Icon class="button-icon" :icon="icon" v-if="icon && !loading" />
      <Icon class="loading button-icon" v-if="loading" icon="loading" size="18"/>
      <div class="s-button-main">
        <slot />
      </div>
    </div>
  </div>
</template>
<script setup>
import Icon from './../icon.vue'
// import { defineProps, defineEmits } from 'vue'
const props = defineProps({
  type:{
    type:String,
    required:false,
    default:'primary',
    validate:value=>{
      if(value){
        const valueFormat = value.toLowerCase()
        return valueFormat === 'primary' || valueFormat === 'default' || valueFormat === 'danger' || valueFormat === 'ghost' || valueFormat === 'dashed'
      }
    }
  },
  size:{
    type:String,
    required:false,
    default:'default',
    validate:value=>{
      if(value){
        const valueFormat = value.toLowerCase()
        return value === 'small' || value === 'large' || value === 'default'
      }
    }
  },
  loading:{
    type:Boolean,
    required:false,
    default:false
  },
  shape:{
    type:String,
    required:false,
    default:'circle',
    validate:value=>{
      if(value){
        const valueFormat = value.toLowerCase()
        return value === 'circle' || value === 'round'
      }
    }
  },
  icon:{
    type:String,
    required:false
  }
})

// const emit = defineEmits(['click'])
// const click = ()=>{
//   emit('click')
// }
const emit = defineEmits(['buttonClick'])
const click = ()=>{
  console.log('测试事件-组件内')
  emit('buttonClick')
}
</script>
<style lang="less">
@import '../_var.less';
*{
  box-sizing: border-box;
}
@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
.s-button{
  cursor: pointer;
  display:inline-block;
  .s-button-content{
    display:flex;
    align-items: center;
    padding:0 16px;
    font-size:@font-size-default;
    height:@button-default-height;
    transition-duration: 0.4s;
    .button-icon{
      order: 1;
      margin-right:0.3em;
      &.loading{
        animation: spin 1s linear infinite;
      }
    }
    .s-button-main{
      order:2;
    }
    &.s-button-content-large{
      padding:0 18px;
      height:@button-default-height;
      font-size:@font-size-large;
    }
    &.s-button-content-small{
      padding:0 14px;
      height:@button-small-height;
    }
    &.s-button-primary{
      background:@main-color;
      color:@main-font-light-color;
      &:hover{
        background:@tint-main-color;
      }
    }
    &.s-button-default{
      background:@button-background;
      border:1px solid @main-color;
      &:hover{
        border:1px solid @tint-main-color;
        color:@main-color;
      }
    }
    &.s-button-danger{
      background:@danger-color;
      color:@main-font-light-color;
      &:hover{
        background:@tint-danger-color;
      }
    }
    &.s-button-ghost{
      background: transparent;
      color:@main-color;
      border:1px solid @main-color;
      &:hover{
        border:1px solid @tint-main-color;
        color:@tint-main-color;
      }
    }
    &.s-button-dashed{
      border:1px dashed @main-color;
      color:@main-color;
      background:@button-background;
      &:hover{
        border:1px dashed @tint-main-color;
        color:@tint-main-color;
      }
    }
  }
}
</style>