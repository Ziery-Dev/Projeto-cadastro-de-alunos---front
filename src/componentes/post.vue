<script setup>
  //importação
  import { onMounted, ref } from "vue";

  //bootstrap
  import 'bootstrap/dist/css/bootstrap.min.css'


  //Vetor de alunos (Onde o mesmo deve ser reativo, pois ao modificar algo no vetor, instnantâneamente a tabela deve alterar tbm)
  let alunos = ref({'id': 0, 'nome': '', 'idade': 0, 'matricula': '', 'curso': ''});

  //visibilidade dos botões
  let visibilidadeBotao = ref(true)

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

      console.log(obj)

    })

    //prevente default(Para que não atualize a página ao clicar no botão de cadastro)
    event.preventDefault();

    
  }

    //função para selecionar um produto

  function selecionar (indice){
      obj.value = {
        id : alunos.value[indice].id,
        nome : alunos.value[indice].nome,
        idade : alunos.value[indice].idade,
        matricula : alunos.value[indice].matricula,
        curso : alunos.value[indice].curso
        
      }

      visibilidadeBotao.value= false;
    }


     //Função de editar aluno (put)
  function editar(){
    //requisicao post
    fetch(`http://localhost:8080/alunos/${obj.value.id}`, {
      method:'PUT',
      body: JSON.stringify(obj.value),
      headers:{'Content-Type':'application/json'}
    })
    .then(requisicao => requisicao.json())
    .then(retorno => {

      //Obter o indice da qual aluno está
      let indiceAluno = alunos.value.findIndex(objA =>{
        return objA.id === retorno.id;
      })

      //Editar o produto na vetor
      alunos.value[indiceAluno] = retorno;

      //limpar o formulário
      obj.value.id = '';
      obj.value.nome = '';
      obj.value.idade = '';
      obj.value.matricula = '';
      obj.value.curso = '';

      //alterar visibilidade dos botões após editar
      visibilidadeBotao.value = true;

    })
  }
     //Função de remover aluno (delete)
  function remover(){
    //requisicao post
    fetch(`http://localhost:8080/alunos/${obj.value.id}`, {
      method:'DELETE',
      headers:{'Content-Type':'application/json'}
    })
  
    .then(() => {

      //Obter o indice da qual aluno está
      let indiceAluno = alunos.value.findIndex(objA =>{
        return objA.id === obj.value.id;
      })

      //Remover o produto no vetor
      alunos.value.splice(indiceAluno, 1);

       //alterar visibilidade dos botões após editar
      visibilidadeBotao.value = true;

      //limpar o formulário
      obj.value.id = 0;
      obj.value.nome = '';
      obj.value.idade = '';
      obj.value.matricula = '';
      obj.value.curso = '';

     

    })
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

    .espacamentoBtn{
      margin-left: 5px;
      margin-right: 5px;
    }
  </style>


 <!--html-->
<template>

  <form @submit="cadastrar">
    <input type="hidden" name="id" id="id" v-model="obj.id">
    <input type="text" placeholder="Nome" name="nome" id="nome" class="form-control" v-model="obj.nome">
    <input type="number" placeholder="Idade" name="idade" id="idade" class="form-control" v-model="obj.idade">
    <input type="text" placeholder="Matrícula" name="matricula" id="matricula" class="form-control" v-model="obj.matricula">
    <input type="text" placeholder="Curso" name="curso" id="curso" class="form-control" v-model="obj.curso">
    <input type="submit" v-if="visibilidadeBotao" class="btn btn-primary" value="Cadastrar">
    <input type="button"  @click="editar" v-if="!visibilidadeBotao" v class="btn btn-warning espacamentoBtn" value="Editar">
    <input type="button" @click="remover" v-if="!visibilidadeBotao" class="btn btn-danger" value="Remover">
   
   
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
      <tr v-for="(a, indice) in alunos" :key="a.id">
        <td>{{a.nome}}</td>
        <td>{{a.idade}}</td>
        <td>{{a.matricula}}</td>
        <td>{{a.curso}}</td>
        <td ><button @click ="selecionar (indice)" class="btn btn-primary" >Selecionar</button></td>
      </tr>
    </tbody>
  </table>

</template>