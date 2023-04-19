<script>
import HeaderCmp from '../components/HeaderCmp.vue';
import Banner from '../components/Banner.vue';
import AboutCard from '../components/AboutCard.vue';
import FooterCmp from '../components/FooterCmp.vue';

import Data from '../data/about.json'
export default {
    components: {
        HeaderCmp,
        Banner,
        AboutCard,
        FooterCmp
    },
    data() {
        return {
            Data: Data
        }
    },
    created() {
        document.title = `Kasa - A propos `
    }
}
</script>

<template>
    <HeaderCmp />
    <div className="cmp-body">
        <Banner />
        <div className="cmp-about-card-container">
            <AboutCard v-for="data, index in Data" :key="index" :title="data.title" :description="data.description" />
        </div>
    </div>


    <FooterCmp />
</template>
