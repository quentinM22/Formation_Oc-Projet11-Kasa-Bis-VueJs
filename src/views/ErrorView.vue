<script>

import HeaderCmp from '../components/HeaderCmp.vue';
import FooterCmp from '../components/FooterCmp.vue';

export default {
    components: { HeaderCmp, FooterCmp },
    created() {

        document.title = `Kasa - Error ❌`;
    },
}
</script>

<template>
    <HeaderCmp />
    <div className="cmp-body">
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
    <FooterCmp />
</template>