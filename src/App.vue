<template>
    <div class="app">
        <h1>Страница с постами</h1>
        <div class="app_btns">
            <my-button
                @click="showDialog"
                
            >
                Создать новый пост

            </my-button>
            <my-select
                v-model="selectedSort"
                :options="sortOptions"
            
            
            />
        </div>
        <my-dialog v-model:show="dialogVisible" >
            <post-form
                @create="createPost"
            />
        </my-dialog>
        <post-list 
            :posts="posts"
            @remove="removePost"
            v-if="!isPostLoading"
        />
        <div v-else>Идет загрузка...</div>
    </div>
</template>


<script>
import PostForm from "@/components/PostForm.vue"
import PostList from "@/components/PostList.vue"
import MyDialog from './components/Ui/MyDialog.vue'
import 'axios'
import axios from 'axios'

export default {
    components: {
        PostList, PostForm,
        MyDialog
    },
    data(){
        return {
            posts: [],
            dialogVisible: false,
            isPostLoading: false,
            selectedSort: '',
            sortOptions: [
                {value: 'title', name: 'По названию'},
                {value: 'body', name: 'По описанию'},
            ]

        }
    },
    methods: {
        createPost(post){
            this.posts.push(post);
            this.dialogVisible = false;
        },
        removePost(post){
            this.posts = this.posts.filter(p => p.id !== post.id)
        },
        showDialog(){
            this.dialogVisible = true;
        },
        async fetchPosts(){
            try {
                this.isPostLoading = true;
                const responce = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10');
                this.posts = responce.data;  
            }catch (e){
                alert('Ошибка')
            }finally {
                this.isPostLoading = false;
            }
        }
    },
    mounted(){
        this.fetchPosts();
    },
    watch: {
        selectedSort(newValue){
            console.log(newValue);
        },
        dialogVisible(newValue){
            console.log(newValue);
        }
    }

}
</script>



<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
.app{
    padding: 20px;
}
.app_btns{
    margin: 15px 0;
    display: flex;
    justify-content: space-between;
}
</style>