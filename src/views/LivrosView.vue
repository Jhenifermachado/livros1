<script>
import { v4 as uuidv4 } from "uuid";
export default {
  data() {
    return {
      livros: [
        {
          id: "c63f9ed0-5077-4dc3-9b9d-268f3fd714f4",
          titulo: "Eu e Esse Meu Coração",
          isbn: "2022006254",
          categoria_id: "1",
          editora_id: "2",
          quantidade: "100",
          preco: "R$ 40,00",
        },
      ],
      novo_livro: "",
      novo_isbn: "",
      novo_categoria_id: "",
      novo_editora_id: "",
      novo_quantidade: "",
      novo_preco: "",
    };
  },
  methods: {
    salvar() {
      const novo_id = uuidv4();
      this.livros.push({
        id: novo_id,
        titulo: this.novo_livros,
        isbn: this.novo_isbn,
        categoria_id: this.novo_categoria_id,
        editora_id: this.novo_editora_id,
        quantidade: this.novo_quantidade,
        preco: this.novo_preco,
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
          placeholder="Titulo"
          v-model="novo_livros"
          @keydown.enter="salvar"
        />
        <input type="text" placeholder="ISBN" v-model="novo_isbn" />
        <input
          type="text"
          placeholder="Categoria_id"
          v-model="novo_categoria_id"
        />
        <input type="text" placeholder="Editora_id" v-model="novo_editora_id" />
        <input type="text" placeholder="Quantidade" v-model="novo_quantidade" />
        <input type="text" placeholder="Preço" v-model="novo_preco" />
        <button @click="salvar">Salvar</button>
      </div>
      <div class="list-livros">
        <table>
          <thead>
            <tr>
              <th>ID</th>
              <th>Titulo</th>
              <th>ISBN</th>
              <th>Categoria_id</th>
              <th>Editora_id</th>
              <th>quantidade</th>
              <th>Preço</th>
            </tr>
          </thead>

          <tbody>
            <tr v-for="livro in livros" :key="livro.id">
              <td>{{ livro.id }}</td>
              <td>{{ livro.titulo }}</td>
              <td>{{ livro.isbn }}</td>
              <td>{{ livro.categoria_id }}</td>
              <td>{{ livro.editora_id }}</td>
              <td>{{ livro.quantidade }}</td>
              <td>{{ livro.preco }}</td>
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
  padding: 0.5rem;
  border: 1px solid black;
  border-radius: 10px;
  background-color: rgb(6, 103, 40);
  color: #fff;
  font-weight: bold;
  margin-left: 1%;
}

.list-livros {
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
