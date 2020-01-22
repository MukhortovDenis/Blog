<template>
    <form @submit.prevent="onSubmit">
        <div class="Registrated">
            <input type="text" placeholder="Имя пользователя" v-model="login" >
            <input type="password" placeholder="Пароль" v-model="password">
            <button type="submit"> Вход </button>
            <button type="button" v-on:click="$emit('open-reg')">Регистрация</button>
        </div>
    </form>
</template>

<script>
    export default {
        name: "HeadReg",
        data(){
            return {
                login: '',
                password: '',
            }
        },
        methods: {
            onSubmit(){

                const users = require('@/data-user.json');
                var bool = false;
                for(let i = 0; i < users.numbUser; i++){
                    if(bool){
                        break;
                    }
                    if (users.dataUser[i].name === this.login && users.dataUser[i].password === this.password){
                        bool = true;
                    }
                }
                if(bool){
                    this.$emit('login-to');
                    this.login = '';
                    this.password = '';
                }
            },
        }
    }
</script>

<style scoped>

</style>