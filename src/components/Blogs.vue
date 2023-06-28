<script setup>
// defineProps(['title', 'body', 'id', 'colorText'])

defineProps ({
    title: String,
    id: Number,
    body: String
    
})
</script>

<template>
    <div class="card">
        <div class="card-body">
            <div class="card-title">
                <h4>{{id}} - {{title}}</h4>  
            </div>
            {{body}}
        </div> 
        <button @click="$emit('añadirFavorito',  title)" class="btn btn-outline-primary">Añadir favorito</button>
    </div>
        
    
</template>