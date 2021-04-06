<template>
  <div :class="{ 'cliente': !isPremiun, 'cliente-premiun': isPremiun }">
    <h3>Produto</h3>
    <p><b>Nome do produto:</b>{{ produto.nome}}</p>
    <p><b>Descrição do produto:</b> {{ produto.descricao }}</p>
    <p><b>Validade do produto:</b>{{ produto.validade }}</p>
    <br/>
    <button @click="mudaCor($event)">Mudar Cor</button>
    <br/>
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
    produto: Object,
  },

  methods:{
    mudaCor: function(){
      this.isPremiun = !this.isPremiun;
    },
    meExcluir: function(){
      // informando ao elemento pai atraves de event que o filho quer ser deletado, pode passar dados como um objeto
      this.$emit("meDelete", {component:this, idFrutaDelete:this.produto.id})
    }
  },
  filters:{
    // CategoriaProduto: function(value){
    //   // deixar o valor em letra maiusculo usando o toUpperCase();
    //   return value();
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

button{
  border-radius: 35px;
  width: 215px;
  height: 30px;
  margin: 4px;
  text-align: center;
  align-items: center;
  background-color: red;
  color: #FFF;
  }

</style>