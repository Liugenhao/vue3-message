<template>
  <div class="child">
    <button @click="childrenClick('来自子组件传来的值')">子组件 Click</button>

    <div>来自父组件传来的值： {{ show }}</div>

  </div>
</template>
<script setup>

  import { ref ,watch } from 'vue'
  
  const test = ref("子组件内容")

  const emit = defineEmits(['childClick'])

  const childrenClick = (data) =>{
    emit('childClick', data)
  }

const props = defineProps({
  show:{
    type:Boolean,
    defulat:false
  }
})
// watch 函数内部调用了 doWatch 函数
// 调用前会在非生产环境下判断第二个参数 cb 是不是一个函数
// 如果不是则会报警告以告诉用户应该使用 watchEffect(fn, options) API
watch (
  () => {
    props.show
  }
)


</script>
<style scoped>

</style>