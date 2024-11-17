
 <!--script-->
<script setup>
import { onMounted, ref } from "vue";


    let texto = ref("Hello World!")


    //Lifecycle onMounted : Após 3 segundos o valor da variavel texto é alterado
    onMounted(()=>{
        setTimeout(()=>{
            texto.value = 'texto alterado';
        }, 3000);
    })
</script>
 
<!--css-->
<style >
  
    

</style>

 <!--html-->
<template>

  <h2> {{texto}} </h2>
    
</template>