<template>
  <div>

    <!-- <input type="text" v-model="produto.nome"> -->
    <h3>Produto</h3>
    <p><b>Nome do produto:</b>{{ produto.nome }}</p>
    <p><b>Descrição do produto:</b> {{ produto.descricao }}</p>
    <p v-if="mostraValid === true"><b>Validade do produto:</b>{{ produto.validade }}</p>
    <p v-else><b> não contem validade!</b></p>

  </div>
</template>

<script>
export default {

  props: {
    mostraValid: Boolean,
    produto: Object,
  },
};
</script>

<style scoped>
div {
  margin: 100px 500px;
  background-color: rosybrown;
  width: 500px;
  height: 300px;
  border-radius: 20px;
  text-align: center;
  padding: 30px;
}

h3 {
  color: pink;
  font-size: 30px;
}
p {
  font-size: 20px;
}
</style>