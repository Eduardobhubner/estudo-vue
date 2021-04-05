<template>
  <div id="app">
    <div id="form">
      <span id="alert-error" v-show="deuErro">Erro ao inserir o nome</span>
      <h3>Cadastrar novas frutas</h3>
      <input type="text" placeholder="Nome da fruta" v-model="nomeField"/>
      <br/>
      <input type="text" placeholder="Descrição da fruta" v-model="descricaoField"/>
      <br/>
      <input type="text" placeholder="Validade da fruta" v-model="validadeField"/>
      <br/>
      <button @click="cadastrar">Cadastrar</button>
    </div>
    <!-- me apresentar as frutas cadastradas através de uma listagem usando o for percorrendo cada uma fruta da lista, como o v-for é ativo, sempre que alguma variavel que ele esta usando é atualizado ele refaz -->
    <div v-for="fruta in frutas" :key="fruta.id">
      <!--evento @meDelete esta escutado oe vendo que  vai ser emitido algo nele pelo componente de sua origem-->
      <Produto :produto="fruta" @meDelete="deletarFruta($event)" />
    </div>
  </div>
</template>

<script>
import Produto from "./components/Produto";

export default {
  name: "App",
  data() {
    return {
      nomeField:"",
      descricaoField:"",
      validadeField:"",
      deuErro: false,
      frutas: [],
    };
  },
  components: {
    Produto,
  },

  methods: {
    cadastrar: function () {
      if (this.nomeField == "" || this.nomeField == " " || this.nomeField.length < 3) {
        this.deuErro = true;
      } else {
        // adicionando objetos ao array frutas
        this.frutas.push({nome: this.nomeField, descricao: this.descricaoField, validade: this.validadeField, id: Date.now()});
        //limpando os campos  
        this.nomeField = "";
        this.descricaoField = "";
        this.validadeField = "";
        this.deuErro = false;
      }
    },
    deletarFruta: function($event){
      var id = $event.idFrutaDelete;
      // criar um filtro, cada elemento dentro do array fruta que tiver o parametro como true, vai permanecer no array, se for false vai ser removido do array
      var novoArrayFrutas = this.frutas.filter(fruta => fruta.id != id);
      this.frutas = novoArrayFrutas;
    }
  },
};
</script>

<style scoped>



#form input{

  width: 200px;
  margin: 3px;
  text-align: center;
  height: 30px;
  border-radius: 20px;
  text-decoration: none;
}

#form button{
  border-radius: 35px;
  width: 215px;
  height: 30px;
  text-align: center;
  align-items: center;
  background-color: green;
  color: #FFF;
  }


#alert-error {
  color: red;
}
</style>
