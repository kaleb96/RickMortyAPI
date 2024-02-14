<script setup>
    import { defineProps } from 'vue';

    const {image, name} = defineProps([
        'image',
        'name',

    ])
</script>

<template>
    <n-card>
        <template #cover>
            <img :src="image">
        </template>
        <h3>{{ name }}</h3>
        <slot></slot>
    </n-card>
</template>

<style scoped>
/* Card Styles */

.n-card {
    width: 200px;
    margin:10px 20px;
    height: 300px;

}
.n-card img {
    height: 250px
}

.jobs {
    display: flex;
    flex-wrap: wrap;
}
</style>