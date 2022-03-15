<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Hello Vue 3 + Vite" />
    <p> {{ child }}</p>
  <div style="margin-bottom:20px;">
    <button @click="pClick">click</button>
  </div>
 
 
  <Child @childClick="childrenClick" :show="isShow"/>


 
</template>

<script setup>

import HelloWorld from './components/HelloWorld.vue'
import Child from './components/child.vue'

import { ref } from 'vue'

const child = ref('')

const isShow = ref(false)

const emit = defineEmits(['childClick'])

const childrenClick = (data) => {
  emit('childClick',data)
  child.value = data
}

const pClick = () =>{
  !isShow.value ? isShow.value = true : isShow.value = false
}

</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
