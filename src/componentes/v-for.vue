 <!--script-->
<script setup>
  let nomes = ["ziery", "tony", "jacyara"]
</script>

 <!--html-->
<template>
<ul>
  <li v-for="nome in nomes">{{nome}}</li>  <!--Percorre e exibe a lista-->
   <!-- v-for="(nome, index) in nomes" v-bind:key="index"-->
</ul>
</template>