 <!--script-->
<script setup>
import { ref } from "vue";

    let texto = ref(''); //ref deixa a variavel reativa, fazendo com que o que for digitado no formulario seja exibido logo abaixo
</script>

 <!--html-->
<template>
<ul>   
    <h2>Insira algo:</h2>
    
    <input type="text" v-model="texto">
    <p>{{texto}}</p>

    <!--v-model é reponsavel por trabalhar com elementos de formulários-->
</ul>
</template>