<template>
  <div>
    <h3>Produto</h3>
    <label for="input-nome">nome:</label>
    <input type="text" id="input-nome" v-model="nome" />
    <br> 
    <label for="input-descricao">Descrição:</label>
    <input type="text" id="input-descricao" v-model="descricao" />
    <hr/>
    <p>Nome do produto: {{ nome }}</p>
    <p>Descrição do produto: {{ descricao }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nome: "Coca-Cola",
      descricao: "bebida destinada ao publico livre",
    };
  },
};
</script>

<style scoped>
div {
  margin: 200px 500px;
  background-color: rosybrown;
  width: 500px;
  height: 300px;
  border-radius: 20px;
  text-align: center;
  padding: 30px;
}

h3{
  color: pink;
  font-size: 30px;
}
p {
  font-size: 20px;
}
</style>