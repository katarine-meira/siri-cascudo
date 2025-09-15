<template>
    <div class="message-container">
        <p>{{msg}}</p>
    </div>
</template>

<script>
    export default{
        name: "MessageComp",
        props:{
            msg: String
        }
    }

</script>

<style scoped>
 .message-container{
    color: #004085;
    background-color: #cce5ff;
    border: 2px solid #B8daff;
    border-radius: 5px;
    padding: 10px;
    margin: 30px;
    text-align: center;
 }
 
</style>