
 <!--script-->
<script setup>
    let validadcao = false;
</script>

<style >
    .ok{
        color: green;
    }
    .falha{
        color: red;
    }

</style>

 <!--html-->
<template>
    <p :class = "validadcao ? 'ok' : 'falha'">Utilizando diretiva class</p> <!--Se a classe validação for true, o nome fica verde, se for false fica vermelho-->
  
    <!--  implementação de classe css classes css-->

</template>