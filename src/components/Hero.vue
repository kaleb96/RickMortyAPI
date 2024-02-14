<script setup>
    import { defineProps, defineEmits } from 'vue';
    
    const {isRickAndMorty} = defineProps([
        'isRickAndMorty'
    ])

    const emit = defineEmits(['selectShow'])

    const emitSelectedShow = () => {
        emit('selectShow');
    }
</script>

<template>
    <div class="hero">
        <h1>{{ isRickAndMorty ? 'Rick and Morty1' : 'Rick and Morty2' }}</h1>
        <p @click="emitSelectedShow">{{ isRickAndMorty ? 'Rick and Morty2' : 'Rick and Morty1' }}</p>
    </div>
</template>

<style scoped>

.hero {
    height : 40vh;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    flex-direction: column
}
.hero img {
    position: absolute;
    height: 700px;
    opacity: 0.1;
}
.hero h1 {
    font-size: 100px;
    font-weight: bold;
}
.hero p {
    cursor: pointer;
}
</style>