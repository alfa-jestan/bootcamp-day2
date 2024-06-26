<template>
    <div>
        <h1 class="text-blue-600">wpisuj dane szczylu</h1>
        <div class="w-100 flex flex-row-reverse">
            <button @click="Pobierzwpisy" class="float-right bg-blue-600 rounded text-white p-10">refresh</button>
        </div>
        pozdrawia ambrorzy co dzieci tworzy
        <div class="grid mx-6 gap-4 my-4">
            <div v-for="(wpis, index) in wpisy" class="drop-shadow-xl bg-stone-300 p-4">
                <p>id: {{ index }}</p>
                <p>{{ wpis }}</p>
                <button  class="bg-blue-600 rounded text-white p-4" @click="deleteWpis(index)">usun</button>
            </div>
        </div>
        <div class="flex justify-center flex-col">
            <input v-model="nowyBlog" type="text" class="border-2 border-blue-400 p-4">
            <button @click="dodajWpis" class="bg-blue-600 rounded text-white p-10">dodaj</button>
        </div>
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
        async Pobierzwpisy() {
            this.wpisy = await day2_backend.odczytaj_wpisy();          
        },
        async dodajWpis() {
            await day2_backend.dodaj_wpis(this.nowyBlog);
            await this.Pobierzwpisy()
        },
        async deleteWpis(index) {
            await day2_backend.usun_wpis(index);
            await this.Pobierzwpisy();
        }
        
    },
    async mounted() {
        this.Pobierzwpisy()
    }
} 
</script>