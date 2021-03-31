<template>
  <div id="app">
    <div id="form">
      <span v-show="deuErro">Erro ao inserir o nome</span>
      <h3>Cadastrar novas frutas</h3>
      <input type="text" placeholder="Nome da fruta" v-model="nomeField" />
      <br />
      <input
        type="text"
        placeholder="Descrição da fruta"
        v-model="descricaoField"
      />
      <br />
      <input
        type="text"
        placeholder="Validade da fruta"
        v-model="validadeField"
      />
      <br />
      <button @click="cadastrar">Cadastrar</button>
    </div>
    <div v-for="fruta in frutas" :key="fruta.id">
      <Produto :produto="fruta" :mostraValid="true" />
    </div>
  </div>
</template>

<script>
import Produto from "./components/Produto";

export default {
  name: "App",
  data() {
    return {
      nomeField: "",
      descricaoField: "",
      validadeField: "",
      deuErro: false,

      frutas: [],
    };
  },

  components: {
    Produto,
  },

  methods: {
    cadastrar: function () {
      if (
        this.nomeField == "" || this.nomeField == " " ||
        this.nomeField.length < 3
      ) {
        this.deuErro = true;
      } else {
        this.frutas.push({ nome: this.nomeField,
          descricao: this.descricaoField,
          validade: this.validadeField,
          id: Date.now(),
        });
        this.nomeField = "";
        this.descricaoField = "";
        this.validadeField = "";
        this.deuErro = false;
      }
    },
  },
};
</script>

<style scoped>
</style>
