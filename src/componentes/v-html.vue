 <!--script-->
<script setup>
  let texto = "<p style = 'color:red' >Aprendendo diretiva v-hmtl</p>";
</script>

 <!--html-->
<template>
<ul>
     <!--Exemplo com interpolação-->
    <div>{{texto}}</div>

    <!--Exemplo com v-html-->
    <div  v-html="texto"></div>

    <!--com v-html a formatação pode ser passada-->
</ul>
</template>