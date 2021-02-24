<template>
    <div>
        <h1>Formulário de login</h1>
        <div class="container">
            <form @submit="submitLogin" method="post">
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
                <button type="submit" class="btn btn-primary">Enviar</button>
            </form>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    methods: {
        submitLogin: function (e) {
            e.preventDefault();
            let data = {
                senha:this.senha,
                email:this.email,
            }

            axios.post('http://localhost:3000/autenticacao/login', data).then((res) => {
                const data = res.data;
                this.$emit('login', data);
            }).catch(function(err){
                console.log(err)
                alert('login falhou')
            })
        }
    },
    data() {
        return {
            email: null,
            senha: null,
        }
    },
}
</script>

<style scoped>
</style>