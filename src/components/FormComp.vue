<template>
    <div>
        <div>
            <message-comp :msg="msg" v-show="msg"/>
            <q-form id="burg" @submit="createBurger">
                <div class="input-container">
                    <label for="nome">Nome do cliente:</label>
                    <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite o seu nome">
                </div>
                <div class="input-container">
                    <label for="pao">Escolha o pão:</label>
                    <select name="pao" id="pao" v-model="pao">
                        <option value="">Selecione seu pão</option>
                        <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">
                            {{ pao.tipo }}
                        </option>
                    </select>
                </div>
                <div class="input-container">
                    <label for="carne">Escolha a carne:</label>
                    <select name="carne" id="carne" v-model="carne">
                        <option value="">Selecione o tipo de carne</option>
                        <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">
                            {{ carne.tipo }}
                        </option>
                    </select>
                </div>
                <div id="opcionais-container" class="input-container">
                    <label id="opcionais-title" for="carne">Selecione os opcionais:</label>
                    <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id">
                        <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
                        <span>{{ opcional.tipo }}</span>
                    </div>
                </div>
                <div class="input-container">
                    <input type="submit" class="submit-btn" value="Criar burger!" >
                </div>
            </q-form>
        </div>
    </div>
    </template>

<script>
import MessageComp from './MessageComp.vue';
    export default{
    components: { MessageComp },
        name: "FormComp",
        data(){
            return{
                paes: null,
                carnes: null,
                opcionaisdata: null,
                nome: null,
                pao: null,
                carne: null,
                opcionais: [],
                
                msg: null
            }
        },
        methods: {
            async getIngredientes(){
                const req = await fetch("http://localhost:3000/ingredientes")
                const data = await req.json();

                this.paes = data.paes;
                this.carnes = data.carnes;
                this.opcionaisdata = data.opcionais;
            },
            async createBurger(e){ //aregumento de evento, quando clicar no submit
                e.preventDefault();  //interrompe o form

                const data = {
                    nome: this.nome,   // é ":" porque estou usando a syntax de objeto do js
                    pao: this.pao,
                    carne: this.carne,
                    opcionais: Array.from(this.opcionais), //metodo para transformar em array
                    status: "solicitado",
                }
                const dataJson = JSON.stringify(data); //transformando json em texto
                
                const req = await fetch("http://localhost:3000/burgers",{
                    method: "POST",
                    headers: {"Content-Type": "application/json"},
                    body: dataJson
                });

                const res = await req.json();

                this.msg = `Pedido Nº ${res.id} realizado com sucesso`

                setTimeout(() => this.msg = "", 3000);
                
                this.nome =" ";
                this.carne="";
                this.pao="";
                this.opcionais="";
            },

            
        },
        mounted(){
            this.getIngredientes()
        }
    }
</script>

<style scoped>
    #burg{
        max-width: 400px;
        margin: 0 auto;
    }

    .input-container{
        display: flex;
        flex-direction: column;
        margin-bottom: 18px;
    }

    label{
        font-weight: bold;
        color: #222;
        margin-bottom: 9px;
        padding: 5px 10px;
        border-left: 4px solid rgb(87, 15, 15);
    }

    input, select{
        padding: 5px 10px;
    }
    
    #opcionais-container{
        flex-direction: row;
        flex-wrap: wrap;
    }

    #opcionais-title{
        width: 100%;
    }

    .checkbox-container{
        display: flex;
        align-items: center;
        width: 50%;
        margin-bottom: 20px;
    }
    
    span{
        margin-left: 5px;
        font-weight: bold;
    }
    .submit-btn{
        background-color: #222;
        color: #FCBA03;
        font-weight: bold;
        border: 2px solid #222;
        padding: 10px;
        cursor: pointer;
        transition: .5s;
        margin-bottom: 80px;
    }
    .submit-btn:hover{
        background-color: transparent;
        color: #222;
    }
</style>