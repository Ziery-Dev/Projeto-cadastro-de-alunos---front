
 <!--script-->
<script setup>
    function mensagem (){
        alert("Você clicou");
    }

    let validacao = true;
</script>

<!--css-->
<style >
    button{
        color: #ffffff;
        background-color: rgb(161, 224, 203);
        border: 1px solid rgb(255, 255, 255);
        border-radius: 10px;
        box-shadow: 1px 1px 2px 0.2px black;
        height: 30px; 
    }
    

</style>

 <!--html-->
<template>
    <button   @click="mensagem">Clique aqui</button>
    <!-- exibindo alerta ao cliar no botão-->

</template>