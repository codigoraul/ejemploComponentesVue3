<script setup>
import { ref} from 'vue'

defineProps(['inicio', 'fin', 'maxLength']);


</script>

<template>
    <div class="btn-group" role="group" aria-label="Basic example">
        <button
         type="button"
          class="btn btn-outline-primary"
          @click="$emit('prev')"
          :disabled="inicio===0"
          >Previous {{ inicio }}</button>

        <button 
        type="button"
         class="btn btn-outline-primary"
         @click="$emit('next')"
         :disabled="fin > maxLength"
         
         >Next {{ fin }}</button>
    </div>
</template>