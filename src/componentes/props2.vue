
 <!--script-->
<script setup>

    const  props = defineProps(['nome', 'idade', 'cidade', 'times', 'funcao'])
   
</script>
 
<!--css-->
<style >
  
    

</style>

 <!--html-->
<template>
    <h1>Nome: {{nome}}</h1>
    <h1>Idade: {{idade}}</h1>
    <h1>Cidade: {{cidade}}</h1>
    <ul>
       <li v-for="time of times">{{time}}</li>
    </ul>
    <button @click="funcao">Clique aqui</button>
  
  
    
</template>