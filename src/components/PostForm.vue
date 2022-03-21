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

        <button 
            class="btn" 
            @click="createPost"
            >
                Создать
        </button>

        <button 
            class="btn"
            @click="deletePost"
            >
            Удалить
        </button>

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
.btn {
    margin-top: 15px;
    align-self: flex-end;
    padding: 18px 30px;
    background: none;
    color: teal;
    border: 1px solid teal;
}
</style>