<script>
import Header from '../components/Header.vue';
import Footer from '../components/Footer.vue';

export default {
    components: { Header, Footer },
    created() {

        document.title = `Kasa - Error ❌`;
    },
}
</script>

<template>
    <div className="cmp-body">
        <Header />
        <div>
            <div className="cmp-error-body">
                <h1 className="cmp-error-title">404</h1>
                <h2 className="cmp-error-subtitle">
                    Oups! La page que vous demandez n'existe pas.
                </h2>
                <router-link to="/">Retourner sur la page d’accueil</router-link>
            </div>
        </div>

    </div>
    <Footer />
</template>