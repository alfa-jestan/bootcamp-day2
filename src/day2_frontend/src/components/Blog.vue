<template>
    <div>
        <button @click="Pobierzwpisy">refresh</button>
        pozdrawia ambrorzy co dzieci tworzy
        {{ wpisy }}
        <input v-model="nowyBlog" type="text">
        <button @click="dodajWpis">dodaj</button>
    </div>
</template>

<script>
import { day2_backend } from 'declarations/day2_backend/index';
export default {
    data() {
        return {
            wpisy: [],
            nowyBlog: ""
        }
    },
    methods: {
        async dodajWpis() {
            await day2_backend.dodaj_wpis(this.nowyBlog);
        },
        async Pobierzwpisy() {
            this.wpisy = await day2_backend.odczytaj_wpisy();          
        }
    }
} 
</script>