<template>
    <div>
        <h1>Formulário de registro</h1>
        <div class="container">
            <form @submit="submitFormulario" method="post">
                <div class="form-group">
                    <label for="nome">Nome</label>
                    <input v-model="nome" type="text" class="form-control" id="nome" placeholder="Digite seu nome">
                </div>
                <br>
                <div class="form-group">
                    <label for="email">Digite seu email</label>
                    <input v-model="email" type="email" class="form-control" id="email" placeholder="Digite seu email">
                </div>
                <br>
                <div class="form-group">
                    <label for="senha">Digite sua senha</label>
                    <input v-model="senha" type="password" class="form-control" id="senha" placeholder="Digite sua senha">
                </div>
                <br>
                <div class="form-group">
                    <label for="senha">Confirme sua senha</label>
                    <input v-model="confirmacao_senha" type="password" class="form-control" id="confirmacao_senha" placeholder="Digite novamente sua senha">
                </div>
                <br>
                <button v-on:click="submitFormulario" type="submit" class="btn btn-primary">Enviar</button>
            </form>
        </div>
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