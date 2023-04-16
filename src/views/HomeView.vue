<script setup>
import Header from '../components/Header.vue';
import Banner from '../components/Banner.vue';
import LocationCard from '../components/LocationCard.vue';
import Footer from '../components/Footer.vue';

import Data from '../data/logements.json'
</script>

<template>
    <div>
        <Header />
        <Banner />
        <div class="cmp-card-container">
                <LocationCard v-for="data, index in Data" :key="index" :title="data.title" :id="data.id"/>
                
            </div>
    </div>
 
 <Footer />
</template>
