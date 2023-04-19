<script>
import FooterCmp from '../components/FooterCmp.vue';
import HeaderCmp from '../components/HeaderCmp.vue';
import Banner from '../components/Banner.vue';
import LocationCard from '../components/LocationCard.vue';


import Data from '../data/logements.json'

export default {
    components: {
        Banner,
        LocationCard,
        FooterCmp,
        HeaderCmp
    },
    data() {
        return {
            Data: Data
        }
    }, created() {

        document.title = `Kasa -  Accueil`;
    },
}
</script>

<template>
    <HeaderCmp />
    <div className="cmp-body">

        <Banner />
        <div class="cmp-card-container">
            <LocationCard v-for="data, index in Data" :key="index" :title="data.title" :id="data.id" :cover="data.cover" />

        </div>
    </div>

    <FooterCmp />
</template>
