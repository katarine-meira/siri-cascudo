<template>
    <banner-comp/>
    <div padding>
        <h1 class="titulo">MONTE SEU HABÚRGUER:</h1>
        <form-comp/>
    </div>
</template>

<script>
import BannerComp from 'src/components/BannerComp.vue'
import FormComp from 'src/components/FormComp.vue'
    export default{
        components: { BannerComp,
                FormComp 

        },
        
        name: 'HomePage',

    }
</script>

<style scoped>
@media (max-width: 800px) {
    .titulo{
        font-size: 25px;
    }
}

</style>