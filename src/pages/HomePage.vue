<template>
    <banner-comp/>
    <div>
        <q-responsive>
            <h1 class="titulo">MONTE SEU HABÚRGUER</h1>
        </q-responsive>
    </div>
</template>

<script>
import BannerComp from 'src/components/BannerComp.vue'
    export default{
        components: { BannerComp 

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