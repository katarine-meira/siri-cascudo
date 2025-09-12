<template>
    <div>
        <q-header>
            <q-toolbar class="bg-black text-white" id="nav">
              <q-item to="/home" class="router_logo">
                <img :src="logo" :alt="alt" id="logo">
              </q-item>
              <router-link to="/pedidos" id="links" >
                Pedidos
              </router-link>
              <router-link to="/home" id="links" >
                Home
              </router-link>
            </q-toolbar>
        </q-header>
    </div>
</template>

<script>
    export default{
        name: 'NavbarComp',
        props: ["logo", "alt"]
    }
</script>

<style scoped>
    #nav{
      display: flex;
      justify-content: flex-end;
      align-items: center;
    }
    .router_logo{
      margin: auto;
      margin-left: 0;
    }
    #logo{
      width: 40px;
      height: 40px;
    }
    #links{
      color: #fcba03;
      text-decoration: none;
      margin: 12px;
    }
    #links:hover{
      color: white;
    }
</style>