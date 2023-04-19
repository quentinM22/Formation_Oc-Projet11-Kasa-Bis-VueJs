<script>
import SlideShow from '../components/SlideShow.vue';
import AboutCard from '../components/AboutCard.vue';
import HeaderCmp from '../components/HeaderCmp.vue';

import Data from '../data/logements.json'
import FooterCmp from '../components/FooterCmp.vue';



export default {
    components: { SlideShow, AboutCard, HeaderCmp, FooterCmp },
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
    <HeaderCmp />
    <div className="cmp-body">
        <div>
            <SlideShow :picture="logement.pictures" />
            <div class="cmp-page-head">
                <div class="cmp-page-title">
                    <h1>{{ logement.title }}</h1>
                    <h2>{{ logement.location }}</h2>
                    <div class="cmp-tag-container">
                        <div v-for="tag, index in logement.tags" class="cmp-tag" :key="index">
                            {{ tag }}
                        </div>
                    </div>
                </div>
                <div class="cmp-page-right">
                    <div class="cmp-page-host">
                        <p>{{ logement.host.name }}</p>
                        <div v-if="logement.host.picture" class="cmp-pics-host"
                            :style="{ backgroundImage: `url(${logement.host.picture || 'grey'})` }">
                        </div>
                    </div>
                    <div class="star-rating">
                        <i class="fa-solid fa-star" v-for="i in 5" :class="{ active: i <= logement.rating }" :key="i"></i>
                    </div>
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

    <FooterCmp />
</template>
<style>
.cmp-page-head {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-top: 20px;
    height: 100%;
}

.cmp-page-title>h1 {
    font-weight: 500;
    font-style: normal;
    font-size: 36px;
    margin: 0;
}

.cmp-page-title>h2 {
    font-weight: 500;
    font-style: normal;
    font-size: 18px;
    margin: 10px 0 10px;
}

.cmp-page-right {
    display: flex;
    flex-direction: column;
}

.cmp-page-host {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    margin: 0 0 15px;
}

.cmp-page-host>p {
    margin-right: 10px;
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
    flex-wrap: wrap;
    margin-top: 10px;
}

.cmp-tag {
    background-color: var(--primary);
    color: white;
    margin: 5px 5px 0 0;
    padding: 5px 40px 5px;
    border-radius: 10px;
    font-size: 20px;
}

.fa-star {
    color: #e3e3e3;
    font-size: x-large;
    margin: 0 5px 0;
}

.active {
    color: var(--primary);
}

.cmp-page-card-container {
    display: flex;
    width: 100%;
    justify-content: space-between;
}

.cmp-page-card {
    width: calc(50% - 10px);
}

.cmp-page-card-container>.cmp-page-card>div>.cmp-AboutCard-btn {
    padding: 13px 20px 13px;
    border-radius: 10px;
}

@media screen and (min-width: 768px) and (max-width: 1023px) {
    .cmp-page-card-container {
        flex-direction: column;
    }

    .cmp-page-card {
        width: 100%;
    }
}

@media screen and (max-width: 767px) {
    .cmp-page-head {
        display: flex;
        flex-direction: column;
        align-items: normal;
    }

    .cmp-page-title>h1 {
        font-size: 18px;
    }

    .cmp-page-title>h2 {
        font-size: 14px;
    }

    .cmp-tag {
        font-size: 10px;
        padding: 5px 20px 5px;
    }

    .cmp-page-right {
        display: flex;
        align-items: center;
        align-items: center;
        flex-direction: row-reverse;
        justify-content: space-between;
        padding: 10px 0 10px;
    }


    .fa-star {
        font-size: medium;
        margin: 0 3px 0;
    }

    .cmp-page-card-container {
        flex-direction: column;
    }

    .cmp-page-card {
        width: 100%;
    }

    .cmp-page-host>p {
        font-size: 12px;
    }

    .cmp-page-card-container>.cmp-page-card>div>.cmp-AboutCard-btn {
        padding: 5px 11px 5px;
    }
}
</style>
