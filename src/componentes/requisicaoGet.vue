<script setup>
import { onMounted, ref } from "vue";

 //Vetor contendo postagens
  let vetor = ref ([]);

  onMounted(()=>{
    fetch('http://localhost:8080/alunos')
    .then(retorno => retorno.json())
    .then(retorno => vetor.value = retorno)
  });

</script>



 <!--html-->
<template>

  <h2>Requisição</h2>
  <table >
    <tr v-for="v in vetor">
      <td>{{v.id}}</td>
      <td>{{v.nome}}</td>
      <td>{{v.idade}}</td>
      <td>{{v.matricula}}</td>
      <td>{{v.curso}}</td>
    </tr>
  </table>
    
</template>