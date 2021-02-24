<template>
    <div>
        <h1>Pagina principal</h1>
        
    </div>
</template>

<script>

import axios from 'axios'

export default {
    methods: {
        submitFormulario: function (e) {
            e.preventDefault();
            let data = {
                senha:this.senha,
                confirmacao_senha:this.confirmacao_senha,
                nome:this.nome,
                email:this.email,
            }
            if(this.senha !== this.confirmacao_senha) {
                return alert('As senhas não conferem!')
            }

            axios.post('http://localhost:3000/autenticacao/registro', data).then(() => {
                alert('usuario cadastrado')
                this.$parent.clickPaginaHome();
            })
            .catch(function(err){
                console.log(err)
            })
        }
    },
    data() {
        return {
            nome: null,
            email: null,
            senha: null,
            confirmacao_senha: null,
        }
    },
}
</script>

<style scoped>
</style>