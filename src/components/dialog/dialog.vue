<template>
  <div class="s-dialog-main" v-if="visible">
    <div class="s-mask"></div>
    <div class="s-dialog-content">
      <div class="s-dialog-header">
        <div v-if="!$slots.title" class="s-title">{{title}}</div>
        <slot v-else name="title" />
        <div class="s-close-dialog" @click="close">×</div>
      </div>
      <div class="s-dialog-body">
        <!-- 没有提供 name 的 <slot> 出口会隐式地命名为“default”。 -->
        <slot />
      </div>
      <div class="s-dialog-footer">
        <div v-if="!$slots.footer" class="s-dialog-footer-button-group">
          <button>确认</button>
          <button @click="close">取消</button>
        </div>
        <slot v-else name="footer"/>
      </div>
    </div>
  </div>
</template>
<script setup>
// ,defineProps,defineEmits
import {ref} from 'vue'

const props = defineProps({
  title:{
    type:[String,Number],
    required:true
  },
  visible:{
    type:Boolean,
    default:false
  }
})
const emitVisble = defineEmits(['update:visible'])
const close = () => {
  emitVisble('update:visible',false)
}
</script>
<style lang="less">
  .s-dialog-main{
    position: relative;
    .s-mask{
      position: fixed;
      top:0;
      left:0;
      right:0;
      bottom:0;
      background:rgba(0,0,0,0.5);
      z-index:2;
    }
    .s-dialog-content{
      position:absolute;
      z-index:3;
      left:50%;
      top:100px;
      transform: translate(-50%,0);
      width:500px;
      background:#fff;
      border-radius:8px;
      .s-dialog-header{
        display:flex;
        justify-content: space-between;
        align-items: center;
        font-weight:500;
        padding:12px;
        border-bottom:1px solid #ccc;
        .s-title{
          text-align:left;
          font-size:16px;
        }
        .s-close-dialog{
          font-size:26px;
          cursor: pointer;
        };
      }
      .s-dialog-body{
        padding:18px;
        border-bottom:1px solid #ccc;
      }
      .s-dialog-footer{
        padding:18px;
        .s-dialog-footer-button-group{
          display:flex;
          justify-content: flex-end;
          align-content: center;
          button{
            padding:10px 16px;
            border:1px solid #ccc;
          }
        }
      }
    }
  }
</style>