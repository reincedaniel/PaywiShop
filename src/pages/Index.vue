<template>
  <q-page class="flex column">



  <VProdutos />



  </q-page>
</template>

<script>
import VProdutos from 'components/Views/V-Produtos'
export default {
  name: 'PageIndex',
  components:{
    VProdutos
  },
  data(){
    return{
     
    }
  },
}
</script>

