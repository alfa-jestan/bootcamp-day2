<template>
    <div>
        <button @click="Pobierzwpisy">refresh</button>
        pozdrawia ambrorzy co dzieci tworzy
        {{ wpisy }}
    </div>
</template>

<script>
import { day2_backend } from 'declarations/day2_backend/index';
export default {
    data() {
        return {
            wpisy: []
        }
    },
    methods: {
        async Pobierzwpisy() {
            this.wpisy = await day2_backend.odczytaj_wpisy()
            
        }
    }
} 
</script>