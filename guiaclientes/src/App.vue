<template>
  <div id="app">
    <div id="form">
      <span id="alert-error" v-show="deuErro">Erro ao inserir o nome</span>
      <!-- nome -->
      <div class="field">
        <label class="label">Nome do produto</label>
        <div class="control">
          <input type="text" class="input" placeholder="Nome da fruta" v-model="nomeField"/>
        </div>
      </div>
      <!-- descriçãos -->
      <div class="field">
        <label class="label">Descrição do produto</label>
        <div class="control">
          <input type="text" class="input" placeholder="Descrição da fruta" v-model="descricaoField"/>        </div>
      </div>
      <!-- validade -->
      <div class="field">
        <label class="label">Validade do produto</label>
        <div class="control">
          <input type="text" class="input" placeholder="Validade da fruta" v-model="validadeField"/>
        </div>
      </div>
      <div class="buttons">
        <button class="button is-success" @click="cadastrar">Cadastrar</button>
      </div>
    </div>
    <!-- me apresentar as frutas cadastradas através de uma listagem usando o for percorrendo cada uma fruta da lista, como o v-for é ativo, sempre que alguma variavel que ele esta usando é atualizado ele refaz -->
    <div v-for="fruta in listarProduto" :key="fruta.id">
      <!--evento @meDelete esta escutado oe vendo que  vai ser emitido algo nele pelo componente de sua origem-->
      <Produto :produto="fruta" @meDelete="deletarFruta($event)" />
    </div>
  </div>
</template>

<script>
import Produto from './components/Produto';
import _ from 'lodash';

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
  computed:{
    listarProduto: function(){
      return _.orderBy(this.frutas,['nome'],['asc']);
    }
  }
};
</script>

<style scoped>

#alert-error {
  color: red;
}
</style>
