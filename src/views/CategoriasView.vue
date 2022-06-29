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
<style>
.title {
  text-align: center;
  margin: 2rem 0;
}

.form-input {
  display: flex;
  justify-content: center;
  margin: 2rem 0;
}

.form-input input {
  width: 50%;
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 10px;
}

.form-input button {
  padding: 0.5rem;
  width: 15%;
  border: 1px solid violet;
  border-radius: 10px;
  background-color: violet;
  color: white;
  font-weight: bold;
  margin-left: 1px;
}

.list-categorias {
  display: flex;
  justify-content: center;
}

table {
  width: 50%;
  border-collapse: collapse;
  margin: 0 auto;
  border: 1px solid black;
  font-size: 1.1rem;
  text-align: center;
}

table thead {
  background-color: rgb(255, 105, 150);
  color: whitesmoke;
  font-size: bold;
}

table thead th {
  background-color: rgb(255, 105, 150);
  color: whitesmoke;
}

table tbody tr:nth-child(odd) {
  background-color: violet;
}
</style>
