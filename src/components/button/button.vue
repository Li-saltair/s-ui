<template>
  <div class="s-button">
    <div class="s-button-content" :class="`s-button-${type}`" :style="{borderRadius:`${sharp.toLowerCase() === 'circle' ?  '4px' : 0}`}">
      <div v-if="icon">
        <Icon :icon="icon" />
      </div>
      <div >
        <slot />
      </div>
    </div>
  </div>
</template>
<script setup>
import Icon from './../icon.vue'
import { defineProps } from 'vue'
const props = defineProps({
  type:{
    type:String,
    required:false,
    default:'primary',
    validate:value=>{
      const valueFormat = value.toLowerCase()
      return valueFormat === 'primary' || valueFormat === 'default' || valueFormat === 'danger' || valueFormat === 'ghost' || valueFormat === 'dashed'
    }
  },
  shape:{
    type:String,
    required:false,
    default:'circle',
    validate:value=>{
      const valueFormat = value.toLowerCase()
      return value === 'circle' || value === 'round'
    }
  },
  icon:{
    type:String,
    required:false
  }
})
</script>
<style lang="less">
@import '../var';
  .s-button{
    .s-button-content{
      &.s-button-primary{
        background:@background;
        color:@button-font;
      }
      &.s-button-default{
        background:@button-bg;
        border:1px solid @background;
      }
      &.s-button-danger{
        background:@red;
        color:@button-font;
      }
      &.s-button-ghost{
        background: transparent;
      }
      &.s-button-dashed{
        border:1px solid #dashed;
      }
    }
  }
</style>