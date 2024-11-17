
 <!--script-->
<script setup>
 import { ref, computed } from 'vue'

  // Páginas
  import Pagina1 from './pagina1.vue'
  import Pagina2 from './pagina2.vue'
  import PaginaErro from './paginaErro.vue'

  // Criar uma estrutura de rotas, contendo o caminho e o camponente
  const routes = {
    '/': Pagina1,
    '/pagina2': Pagina2,
    '/404': PaginaErro
  }

  // Obter o conteúdo a partir da cerquila, exemplo: http://localhost:5173/#/sobre o retorno será: #/sobre
  const referenciaRota = ref(window.location.hash)

  // Executa a ação quando realizar a navegação entre páginas. Obter o conteúdo a partir da cerquilha
  window.addEventListener('hashchange', () => {
    referenciaRota.value = window.location.hash
  });

  // Função responsável por exibir a página específica
  const currentView = computed(() => {
    return routes[referenciaRota.value.slice(1) || '/'] || PaginaErro
  })

</script>
 


 <!--html-->
<template>
 <!-- Links -->
  <a href="#/">Página 1</a>
  |
  <a href="#/pagina2">Página 2</a>

  <!-- Exibição das páginas -->
  <component :is="currentView" />
    
</template>
