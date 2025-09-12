<template>
    <div id="banner">
        <h1 text-h1 text-md-h3>Monte Seu Hambúrguer</h1>
    </div>
</template>

<script>
    export default{
        nome: 'BannerComp',
    }
</script>

<style scoped>
    #banner{
        background-image: url('/public/icons/burger.jpg');
        background-position: center center; /* centraliza horizontal e vertical */
        background-size: cover;
        display: flex;
        align-items: center;
        justify-content: flex-start;
        height: 70vh;
        background-repeat: no-repeat;
    }

</style>