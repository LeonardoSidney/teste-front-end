<template>
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <div class="navbar-collapse mr-auto ml-auto">
            <a class="navbar-brand" href="#">{{pagina}}</a>
            <ul class="navbar-nav mr-auto">
                <li class="nav-item">
                    <a v-on:click="clickPaginaHome" class="nav-link" href="#">Home</a>
                </li>
                <li v-if="showLogin" class="nav-item">
                    <a v-on:click="clickPaginaLogin" class="nav-link" href="#">Login</a>
                </li>
                <li v-if="showRegistro" class="nav-item">
                    <a v-on:click="clickPaginaRegistro" class="nav-link" href="#">Register</a>
                </li>
            </ul>
        </div>
    </nav>
</template>

<script>
export default {
    components: {
    },
    props: {
        pagina: String,
        showLogin: Boolean,
        showRegistro: Boolean,
    },
    methods: {
        clickPaginaLogin: function () {
            this.$parent.clickPaginaLogin();
        },
        clickPaginaHome: function () {
            this.$parent.clickPaginaHome();
        },
        clickPaginaRegistro: function () {
            this.$parent.clickPaginaRegistro();
        }
    },
}
</script>

<style scoped>
    .navbar-collapse {
        margin-left: 40px;
    }
</style>