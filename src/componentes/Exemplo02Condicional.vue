 <!--script-->
<script setup>
  let exibir = true; //variavel booleana 
</script>

 <!--html-->
<template>
  <h2 v-if="exibir">Hello world</h2> <!--O que a variave exibir é passada para o v-if, true exibe o hello world, false não exibe-->
</template>