
 <!--script-->
<script setup>

    function validaForm (){
        alert("fomulário enviado");
    }

    let validacao = true;
</script>

<!--css-->
<style >
  
    

</style>

 <!--html-->
<template>
<h2>Clique para enviar</h2>
    <form action="enviar"  @submit="validaForm"> <!--@submit recebe a função de alerta, que pode ser função para enviar a informação digitado para outro local-->
        <input type="submit" value="Enviar formulário">
    </form>
    
</template>