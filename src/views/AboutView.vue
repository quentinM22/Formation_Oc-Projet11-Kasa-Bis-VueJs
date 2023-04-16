<script setup>
import Header from '../components/Header.vue';
import Banner from '../components/Banner.vue';
import AboutCard from '../components/AboutCard.vue';
import Footer from '../components/Footer.vue';

import Data from '../data/about.json'

</script>

<template>
    <div className="cmp-body">
        <Header />
        <Banner />
        <div className="cmp-about-card-container">
                <AboutCard v-for="data, index in Data"
                 :key="index"
                 :title="data.title"
                 :description="data.description" />
            </div>
        </div>
        
 
 <Footer />
</template>
