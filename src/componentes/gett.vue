<script setup>
  //importação
  import { onMounted, ref } from "vue";

  //bootstrap
  import 'bootstrap/dist/css/bootstrap.min.css'


  //Vetor de produtos (Onde o mesmo deve ser reativo, pois ao modificar algo no vetor, instnantâneamente a tabela deve alterar tbm)
  let alunos = ref([]);


  //onMounted
  onMounted(() => {
    fetch('http://localhost:8080/alunos')
    .then(requisicao => requisicao.json())
    .then(retorno => alunos.value = retorno);
  })


</script>





 <!--css-->
  <style >
    form{
      width: 50%;
      margin: 30px auto;
      text-align: center;
    }

    form input{
      margin-bottom: 10px;
    }

    table{
      margin: 30px;
    }
  </style>


 <!--html-->
<template>

  <form>
    <input type="text" placeholder="Aluno" name="aluno" id="aluno" class="form-control">
    <input type="number" placeholder="Idade" name="idade" id="idade" class="form-control">
    <input type="text" placeholder="Matrícula" name="matricula" id="matricula" class="form-control">
    <input type="text" placeholder="Curso" name="curso" id="aluno" class="form-control">
    <input type="submit" class="btn btn-primary" value="Cadastrar">

    
  </form>

  <table class="table table-striped">
    <thead>
      <tr>
        <th>Nome</th>
        <th>Idade</th>
        <th>Matrícula</th>
        <th>Curso</th>
        <th>Selecionar</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="a in alunos" :key="a.id">
        <td>{{a.nome}}</td>
        <td>{{a.idade}}</td>
        <td>{{a.matricula}}</td>
        <td>{{a.curso}}</td>
        <td ><button class="btn btn-primary" >Selecionar</button></td>
      </tr>
    </tbody>
  </table>


    <!--O que foi feito?
    1- o consumo gett da minha api na parte do script
    2 - as informações da api foram passadas a tabela utilizando o v-for no vetor que continha os dados da api, vetor esse que é reativo, para que qulquer alteração seja atulizada isntantanemente na tabela
    3 - :key foi utilizado para identificar o id
    4 - importação do bootStrap, fazendo uso de algumas classes do boot Strap para estilizar a tabela e botões

    
    -->
</template>