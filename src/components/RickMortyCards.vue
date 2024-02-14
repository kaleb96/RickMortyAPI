<script setup>
    import axios from 'axios';
    import { ref, watch, onMounted } from 'vue'; 
    import Card from './Cards.vue'

    const characters = ref(null)
    const page = ref(1);
    
    onMounted(async () => {
        
        const response = await axios.get('https://rickandmortyapi.com/api/character');
        setTimeout(() => {
            characters.value = response.data.results
        }, 1500);
    }) 

        watch(page, async ()=> {
            characters.value = null;
            const res = await axios.get(`https://rickandmortyapi.com/api/character?page=${page.value}`);
            setTimeout(() => {
                characters.value = res.data.results
        }, 1500);
            
    })

</script>
<template>
    <div class="container">
        <div class="cards" v-if="characters">
            <Card
                v-for="character in characters"
                :key="character.id"
                :image="character.image"
                :name="character.name"
            >
                <p>{{ character.location.name }}</p>
            </Card>
        </div>
        <div v-else class="cards spinner">
            <n-spin size="large"/>
        </div>
        <div class="button-container">
            <button @click="page--">&lt</button>
            <button @click="page++">&gt</button>
        </div>
    </div>
</template>

<style scoped>
/* Breaking Bad Styles */

.container {
    background-color: rgb(27, 26, 26);
    padding: 30px
}
.cards {
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
 
}
.cards h3 {
    font-weight: bold;
}
.cards p {
    font-size: 10px;
}
.jobs {
    display: flex;
    flex-wrap: wrap;
}
.button-container {
    display: flex;
    justify-content: center;
    padding-top: 30px
}
.button-container button {
    border: none;
    width: 50px;
    height: 50px;
    border-radius: 100%;
    margin: 0 5px;
    cursor: pointer;
}
.spinner {
    display: flex;
    align-items: center;
    justify-content: center;
}

</style>