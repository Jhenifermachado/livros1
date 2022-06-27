<script>
import { v4 as uuidv4 } from "uuid";
export default {
  data() {
    return {
      categorias: [
        {
          id: "bc79618d-dd80-456d-a11d-f9c14db9eebf",
          categorias: "Romance",
        },
      ],
      novo_categorias: "",
    };
  },
  methods: {
    salvar() {
      if (this.novo_categorias !== "") {
        const novo_id = uuidv4();
        this.categorias.push({
          id: novo_id,
          categorias: this.novo_categorias,
        });
      }
    },
    excluir(categorias) {
      const indice = this.categorias.indexOf(categorias);
      this.categorias.splice(indice, 1);
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="title">
      <h2>Categorias</h2>
    </div>
    <div class="form-input">
      <input type="text" v-model="novo_categorias" @keydown.enter="salvar" />
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-categorias">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Categorias</th>
            <th></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="categorias in categoria" :key="categorias.id"></tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
