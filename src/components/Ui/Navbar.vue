<template>
    <div class="navbar">
        <div @click="$router.push('/')" style="margin-left: 20px" >Соцсеть</div>
        <div class="navbar_btns">
            <my-button @click="$router.push('/posts')">Посты</my-button>
            <my-button style="margin-left: 20px" @click="$router.push('/about')">О нас</my-button>
        </div>
    </div>
</template>

<script>

export default {

}
</script>

<style scoped>
.navbar{
    height: 60px;
    background-color: rgb(224, 224, 224);
    box-shadow: 2px 2px 4px gray;
    display: flex;
    align-items: center;
    padding: 0x 15px;
}
.navbar_btns{
    margin-left: auto;
}
</style>
