<template>
  <div id="app">
    <!-- <Produto :cliente="mercadoria" /> -->
    <!-- <Produto nome="Laranja" descricao="Teste" validade="25-03-2021"/> -->
    <Produto :produto="mercadoria" :mostraValid="false" />
    <Produto :produto="fruta" :mostraValid="true" />
    
  </div>
</template>

<script>
import Produto from "./components/Produto";

export default {
  name: "App",
  data() {
    return {
      mercadoria: {
        nome: "Madeira",
        descricao: "Usado em construção e objetos",
        validade: "Não possui",
      },
      fruta: {
        nome: "Banana",
        descricao: "Bom para a saúde",
        validade: "Até 2 semanas depois de sua colheita",
      },
    };
  },

  components: {
    Produto,
  },
};
</script>

<style scoped>
</style>
