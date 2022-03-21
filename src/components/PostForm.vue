<template>
    <form @submit.prevent> 
        <h4>Создание поста</h4>
        <input
            v-model="post.title"
            class="input" 
            type="text" 
            placeholder="Название"
        >
        <input 
            v-model="post.body"
            class="input" 
            type="text" 
            placeholder="Описание"
        >

        <my-button
            style="align-self: flex-end; margin-top: 15px"
            @click="createPost"
            >
                Создать
        </my-button>

        <my-button
            style="align-self: flex-end; margin-top: 15px"
            @click="deletePost"
            >
            Удалить
        </my-button>

    </form>
</template>

<script>
export default {
    data() {
        return {
            post: {
                title: '',
                body: ''
            }
        }
    },
    methods: {
        createPost() {
            this.post.id = Date.now();
            this.$emit('create', this.post)
            this.post = {
                title: '',
                body: ''
            }
        },
        deletePost(){
            this.$emit('delete', this.post)
        }
    }
}
</script>

<style scoped>
form{
    display: flex;
    flex-direction: column;
}
.input {
    width: 100%;
    border: 2px solid teal;
    padding: 18px 15px;
    margin-top: 15px;
    }

</style>