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

watch (
  () => {
    props.show
  }
)


</script>
<style scoped>

</style>