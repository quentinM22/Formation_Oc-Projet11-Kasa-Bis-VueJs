<script>
import Header from '../components/Header.vue';
import Banner from '../components/Banner.vue';
import LocationCard from '../components/LocationCard.vue';
import Footer from '../components/Footer.vue';

import Data from '../data/logements.json'
export default{
    components: {
        Header,
        Banner,
        LocationCard,
        Footer
    },
    data(){
        return{
            Data: Data
        }
    }
}
</script>

<template>
    <div className="cmp-body">
        <Header />
        <Banner />
        <div class="cmp-card-container">
                <LocationCard v-for="data, index in Data" :key="index" :title="data.title" :id="data.id"/>
                
            </div>
    </div>
 
 <Footer />
</template>
