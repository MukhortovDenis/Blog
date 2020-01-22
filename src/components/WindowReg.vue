<template>
    <div class="b-popup">
        <div class="b-popup-content">
            <form @submit.prevent="onSubmit">

                <h3>Введите логин</h3>
                <input type="text" placeholder="Введите ваш логин" v-model="login">
                <h3>Введите пароль</h3>
                <input type="password" placeholder="Ваш пароль" v-model="password">
                <hr>
                <button type="submit">Зарегистрироваться</button>
            </form>
        </div>
    </div>
</template>

<script>
    export default {
        name: "WindowReg",
        data(){
            return {
                login: '',
                password: ''
            }
        },
        methods: {
            onSubmit(){

                const users = require('@/data-user.json');
                var bool = true;
                for(let i = 0; i < users.numbUser; i++){
                    if(this.login === users.dataUser[i].name){bool = false;}}
                if(bool) {
                    const user = {
                        name: this.login,
                        password: this.password
                    };
                    users.dataUser.push(user);
                    users.numbUser++;
                    // eslint-disable-next-line no-console
                    console.log(users);
                    this.$emit('success-reg');
                    this.password = '';
                    this.login = ''
                }
            }
        }
    }
</script>

<style scoped>

</style>