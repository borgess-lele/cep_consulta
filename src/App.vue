<script>
import axios from "axios";
export default {
  data() {
    return {
      cep: "",
      endereco: {},
    };
  },
  methods: {
    async buscar() {
      const url = `https://viacep.com.br/ws/${this.cep}/json/`;
      const { data } = await axios.get(url);
      this.endereco = data;
    },
  },
};
</script>
<template>
  <div class="form">
    <h1>Buscar Cep</h1>
    <p>Digite o cep:</p>
    <input type="text" v-model="cep" placeholder="xxxxxxxx" />
    <button @click="buscar">Buscar</button>
  </div>
  <form>
    <input
      name="rua"
      type="text"
      v-model="endereco.logradouro"
      placeholder="Rua"
    />
    <input
      name="bairro"
      type="text"
      v-model="endereco.bairro"
      placeholder="Bairro"
    />
    <input
      for="localidade"
      type="text"
      v-model="endereco.localidade"
      placeholder="Localidade"
    />
    <input
      for="estado"
      type="text"
      v-model="endereco.uf"
      placeholder="Estado"
    />
  </form>
</template>
<style>
input {
  max-width: 1000px;
  margin: 150 auto;
  padding: 8px;
  font-weight: normal;
  height: 10px;
}
</style>
