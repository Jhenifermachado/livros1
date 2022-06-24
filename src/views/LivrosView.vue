<script>
import { v4 as uuidv4 } from "uuid";
export default {
  data() {
    return {
      livros: [
        {
          id: "c63f9ed0-5077-4dc3-9b9d-268f3fd714f4",
          livros: "Eu e Esse Meu Coração",
          categorias: "",
          paginas: "",
        },
      ],
      novo_livro: "",
      novo_categorias: "",
      novo_paginas: "",
    };
  },
  methods: {
    salvar() {
      const novo_id = uuidv4();
      this.livros.push({
        id: novo_id,
        livros: this.novo_livros,
        categorias: this.novo_categorias,
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
        <input type="text" placeholder="categorias" v-model="novo_categorias" />
        <input type="text" placeholder="paginas" v-model="novo_paginas" />
        <button @click="salvar">Salvar</button>
      </div>
      <div class="list-categorias">
        <table>
          <thead>
            <tr>
              <th>ID</th>
              <th>Livros</th>
              <th>categorias</th>
              <th>paginas</th>
            </tr>
          </thead>

          <tbody>
            <tr v-for="livro in livros" :key="livro.id">
              <td>{{ livro.id }}</td>
              <td>{{ livro.livros }}</td>
              <td>{{ livro.categorias }}</td>
              <td>{{ livro.paginas }}</td>
              <td>???</td>
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

