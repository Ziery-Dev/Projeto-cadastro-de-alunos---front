
 <!--script-->
<script setup>

    function mensagem (){
        alert("teclou");
    }

    let validacao = true;
</script>

<!--css-->
<style >
  
    

</style>

 <!--html-->
<template>
<h2>Digite alguma coisa:</h2>
   <input type="text" @keyup.enter="mensagem"> <!--Ao clicar no botão especificado, chama a função que exibe um alerta com a mensagem (essa função pode ser outra coisa) -->

</template>