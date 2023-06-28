<script setup>
import {ref} from 'vue'

const counter = ref(0)
const contador = () =>{
  counter.value++
  return
}
</script>
<template>
    
  <button @click="contador">
    Contador {{ counter }}
  </button>
</template>