 <!--script-->
<script setup>
  let exibir = true; //variavel booleana 
  let media = 9;
</script>

 <!--html-->
<template>
  <h2 v-if="exibir">Hello world</h2> 
    <p v-if="media >= 8">Aprovado</p>
    <p v-else-if="media >=5">Em exame</p>
    <p v-else>Reprovado</p>
    
    <!--Fazendo uma verificação simples usando v-if/v/else-if para saber se um aluno foi aprovado, em exame ou reprovado-->
</template>