<template>
  <q-layout view="hHh LpR lFf" class="tma" >
    <navbar-comp :logo="logo_src" :alt="alt_name"/>
    <q-page-container>
      <router-view></router-view>
    </q-page-container>
    <footer-comp/>
  </q-layout>
</template>

<script>
import NavbarComp from "src/components/NavbarComp.vue";
import FooterComp from 'src/components/FooterComp.vue';

    export default {
    components: { 
      NavbarComp,
      FooterComp,

    },
    data(){
      return{
        logo_src: "/public/icons/logo.png",
        alt_name: "Hamburgueiria"
      }
    }
  }
</script>

<style>
*{
  font-family: helvetica;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-weight: bold;
  
}


h1{
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: #222;
}
</style>