<template>
    <div class="title">{{ username }}'s Shopping Cart</div>
</template>

<script>
    export default {
        //receive from parent component (ShoppingCart)
        props: ['username'],
    };
</script>

<style scoped> 
    .title {
        background-color: purple;
        height: 50px;
        line-height: 50px;
        text-align: center;
        font-size: 30px;
        color: aliceblue;
    }
</style>