<template>
    <div class="b-popup">
        <div class="b-popup-content">
            <form @submit.prevent="onSubmit">
                <button type="submit">Выход</button>
                <br>
                <textarea v-model="text"> </textarea>
            </form>
        </div>
    </div>
</template>

<script>
    export default {
        name: "WindowEdit",
        data(){
            return{
                textId: require('@/data-post.json').idNow,
                text: require('@/data-post.json').posts[require('@/data-post.json').idNow].content
            }
        },
        methods: {
            onSubmit(){
                const post = require('@/data-post.json');
                post.posts[this.textId].content = this.text;
                // eslint-disable-next-line no-console
                console.log(this.text);
                this.$emit('close-edit');
            }
        },
    }
</script>

<style scoped>
    *{
        font-family: Areal;
    }
    textarea{
        width: 99.4%;
        height: 240%;
        font-family: 'Merriweather', serif;
    }

</style>