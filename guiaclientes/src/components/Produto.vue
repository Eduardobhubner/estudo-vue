<template>
  <div :class="{ 'cliente': !isPremiun, 'cliente-premiun': isPremiun }">
    <h3>Produto</h3>
    <p><b>Nome do produto:</b>{{ produto.nome }}</p>
    <p><b>Descrição do produto:</b> {{ produto.descricao }}</p>
    <p v-if="mostraValid === true">
      <b>Validade do produto:</b>{{ produto.validade }}
    </p>
    <p v-else><b> não contem validade!</b></p>
    <button @click="mudaCor">Mudar Cor</button>
    <br>
    <button @click="meExcluir">Excluir</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isPremiun: false,
    };
  },

  props: {
    mostraValid: Boolean,
    produto: Object,
  },

  methods:{
    mudaCor: function(){
      this.isPremiun = !this.isPremiun;
    },

    // meExcluir: function(){
    //   console.log("quero ser excluido");
    //   this.$emit("meDelete",{idDaFruta: this.fruta.id})
    // }
  }
};
</script>

<style scoped>
.cliente {
  margin: 50px 2%;
  background-color: rosybrown;
  width: 500px;
  height: 300px;
  border-radius: 20px;
  /* text-align: center; */
  padding: 30px;
}

.cliente-premiun {
  margin: 50px 2%;
  background-color: yellow;
  width: 500px;
  height: 300px;
  border-radius: 20px;
  /* text-align: center; */
  padding: 30px;
}

h3 {
  color: #444;
  font-size: 30px;
}
p {
  font-size: 20px;
}
</style>