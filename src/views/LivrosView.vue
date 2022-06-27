<script>
import { v4 as uuidv4 } from "uuid";
export default {
  data() {
    return {
      livros: [
        {
          id: "c63f9ed0-5077-4dc3-9b9d-268f3fd714f4",
          livros: "Eu e Esse Meu Coração",
          paginas: "210",
        },
      ],
      novo_livro: "",
      novo_paginas: "",
    };
  },
  methods: {
    salvar() {
      const novo_id = uuidv4();
      this.livros.push({
        id: novo_id,
        livros: this.novo_livros,
        paginas: this.novo_paginas,
      });
    },
  },
};
</script>

<template>
  <main>
    <div class="conteiner">
      <div class="title">
        <h2>Gerenciamento de livros</h2>
      </div>
      <div class="form-input">
        <input
          type="text"
          placeholder="livros"
          v-model="novo_livros"
          @keydown.enter="salvar"
        />
        <input type="text" placeholder="paginas" v-model="novo_paginas" />
        <button @click="salvar">Salvar</button>
      </div>
      <div class="list-paginas">
        <table>
          <thead>
            <tr>
              <th>ID</th>
              <th>Livros</th>
              <th>paginas</th>
              <th></th>
            </tr>
          </thead>

          <tbody>
            <tr v-for="livro in livros" :key="livro.id">
              <td>{{ livro.id }}</td>
              <td>{{ livro.livros }}</td>
              <td>{{ livro.paginas }}</td>
              <td></td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </main>
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
  padding: 00.5rem;
  border: 1px solid black;
  border-radius: 10px;
  background-color: rgb(6, 103, 40);
  color: #fff;
  font-weight: bold;
  margin-left: 1%;
}

.list-paginas {
  display: flex;
  justify-content: center;
}

table {
  width: 80%;
  border-collapse: collapse;
  margin: 0 auto;
  border: 1px solid black;
  font-size: 1.1rem;
  text-align: center;
}

table thead {
  background-color: rgb(255, 105, 180);
  color: whitesmoke;
  font-size: bold;
}

table thead th {
  background-color: rgb(255, 105, 180);
  color: whitesmoke;
}

table tbody tr:nth-child(odd) {
  background-color: violet;
}
</style>
