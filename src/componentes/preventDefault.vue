
 <!--script-->
<script setup>

    function validaForm (event){
        alert("fomulário enviado");
        event.preventDefault(); //A adição desse event.preventDefault() evita que apos o envio do formulario, a pagina não redicione ao url para qual os dados foram enviados
    }

    let validacao = true;
</script>
 
<!--css-->
<style >
  
    

</style>

 <!--html-->
<template>
<h2>Clique para enviar</h2>
    <form action="https://www.youtube.com"  @submit="validaForm"> <!--aqui o url passado em action especifica para onde os dados seraão enviado-->
        <input type="submit" value="Enviar formulário">
    </form>
    
</template>