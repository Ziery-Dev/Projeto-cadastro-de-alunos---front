<script setup>
  //importação
  import { onMounted, ref } from "vue";

  //bootstrap
  import 'bootstrap/dist/css/bootstrap.min.css'


  //Vetor de produtos (Onde o mesmo deve ser reativo, pois ao modificar algo no vetor, instnantâneamente a tabela deve alterar tbm)
  let alunos = ref({'id': 0, 'aluno': '', 'idade': 0, 'matricula': '', 'curso': ''});


  //onMounted
  onMounted(() => {
    fetch('http://localhost:8080/alunos')
    .then(requisicao => requisicao.json())
    .then(retorno => alunos.value = retorno);
  })

  //Objeto produto
  let obj = ref({}); 
  
  //Função de cadastro (Post)
  function cadastrar(event){
    //requisicao post
    fetch('http://localhost:8080/alunos', {
      method:'POST',
      body: JSON.stringify(obj.value),
      headers:{'Content-Type':'application/json'}
    })
    .then(requisicao => requisicao.json())
    .then(retorno => {
      //cadastrar o produto na vetor
      alunos.value.push(retorno)

      //limpar o formulário
      obj.value.nome = '';
      obj.value.idade = '';
      obj.value.matricula = '';
      obj.value.curso = '';

    })

    //prevente default(Para que não atualize a página ao clicar no botão de cadastro)
    event.preventDefault();

  }
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

  <form @submit="cadastrar">
    <input type="text" placeholder="Aluno" name="aluno" id="aluno" class="form-control" v-model="obj.nome">
    <input type="number" placeholder="Idade" name="idade" id="idade" class="form-control" v-model="obj.idade">
    <input type="text" placeholder="Matrícula" name="matricula" id="matricula" class="form-control" v-model="obj.matricula">
    <input type="text" placeholder="Curso" name="curso" id="curso" class="form-control" v-model="obj.curso">
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

</template>