<script>
import Header from '../components/Header.vue';
import Footer from '../components/Footer.vue';
import SlideShow from '../components/SlideShow.vue';
import AboutCard from '../components/AboutCard.vue';


import Data from '../data/logements.json'


export default {
    components: { Header, Footer, SlideShow, AboutCard },
    data() {
        return {
            logement: null,
        };
    },
    // Gestion de la page Erreur
    beforeRouteEnter(to, from, next) {
        const { id } = to.params;
        const logement = Data.find((item) => item.id === id.split(":id")[1]);
        if (!logement) {
            next({ path: '/Erreur' });
        } else {
            next();
        }
    },
    // Récuperation de logement
    created() {
        const { id } = this.$route.params;
        this.logement = Data.find((item) => item.id === id.split(":id")[1]);
        document.title = `Kasa -  ${this.logement.title}`;
    },
}

</script>

<template>
    <div className="cmp-body">
        <Header />
        <div>
            <SlideShow :picture="logement.pictures" />
            <div class="cmp-page-head">
                <div class="cmp-page-title">
                    <h1>{{ logement.title }}</h1>
                    <h2>{{ logement.location }}</h2>
                </div>
                <div class="cmp-page-host">
                    <p>{{ logement.host.name }}</p>

                    <div v-if="logement.host.picture" className="cmp-pics-host"
                        :style="{ backgroundImage: `url(${logement.host.picture || 'grey'})` }"></div>

                </div>
            </div>
            <div class="cmp-page-head">
                <div class="cmp-tag-container">
                    <div v-for="tag, index in logement.tags" class="cmp-tag" :key="index">
                        {{ tag }}
                    </div>
                </div>
                <div>
                    <div class="star-rating">
                        <i class="fa-solid fa-star" v-for="i in 5" :class="{ active: i <= logement.rating }" :key="i"></i>
                    </div>
                </div>
            </div>
            <div class="cmp-page-card-container">
                <div class="cmp-page-card">
                    <AboutCard title="Description" :description="logement.description" />
                </div>

                <div class="cmp-page-card">
                    <AboutCard title="Équipements" :list="logement.equipments" />
                </div>
            </div>

        </div>
    </div>

    <Footer />
</template>
<style>
.cmp-page-head {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.cmp-page-title>h1 {
    font-weight: 500;
    font-style: normal;
    font-size: 36px;
    margin-bottom: 0;
}

.cmp-page-title>h2 {
    font-weight: 500;
    font-style: normal;
    font-size: 18px;
    margin-top: 10px;
}

.cmp-page-host {
    display: flex;
    align-items: center;
    justify-content: flex-end;
}

.cmp-page-host>p {
    padding: 0 5px 0;
    width: 70px;
    text-align: end;
}

.cmp-page-host>.cmp-pics-host {
    border-radius: 100%;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    height: 64px;
    width: 64px;
}

.cmp-tag-container {
    display: flex;
    align-items: center;
    margin-top: 10px;
}

.cmp-tag {
    background-color: #ff6060;
    color: white;
    margin-right: 10px;
    padding: 5px 40px 5px;
    border-radius: 10px;
}

.fa-star {
    color: #e3e3e3;
    font-size: x-large;
    margin: 0 5px 0;
}

.active {
    color: #ff6060;
}

.cmp-page-card-container {
    display: flex;
    width: 100%;
    justify-content: space-between;
}

.cmp-page-card {
    width: calc(50% - 10px);
}
</style>
