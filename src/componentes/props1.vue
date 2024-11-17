
 <!--script-->
<script setup>

    import props2 from './props2.vue'

    //variaveis
    let cidade = 'Monção'
    let times = ["flamengo", "vasco", "corinthians"]

    //Funções
    function mensagem(){
        alert('Função exemplo');
    }

</script>
 
<!--css-->
<style >
  
    

</style>

 <!--html-->
<template>

 <props2 nome = 'ziery' idade = '25' :cidade = 'cidade' :times = 'times' :funcao='mensagem'> </props2> <!--Ao passar uma variavel como props, deve-se adicionar os : na frente do nome da variavel-->
    
</template>
