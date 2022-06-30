<script>
import { v4 as uuidv4 } from "uuid";
export default {
  data() {
    return {
      editoras: [
        {
          id: "53f2873b-892c-4cc6-b30f-de269626e9d2",
          nome: "Globo Livros",
          site: "http://globolivros.globo.com/",
        },
      ],
      novo_editora: "",
    };
  },
  methods: {
    salvar() {
      if (this.novo_editora !== "") {
        const novo_id = uuidv4();
        this.editoras.push({
          id: novo_id,
          nome: this.novo_editora,
        });
      }
    },
    excluir(editora) {
      const indice = this.editoras.index0f(editora);
      this.editoras.splice(indice, 1);
    },
  },
};
</script>
<template>
  <div class="container">
    <div class="title">
      <h2>Editoras</h2>
    </div>
    <div class="form-input">
      <input type="text" v-model="novo_editora" @keydown.enter="salvar" />
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-editoras">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th>Site</th>
            <th></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="editora in editoras" :key="editora.id">
            <td>{{ editora.id }}</td>
            <td>{{ editora.nome }}</td>
            <td>{{ editora.site }}</td>
            <td>
              <button>Editar</button>
              <button @click="excluir(editora)">excluir</button>
            </td>
          </tr>
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

.list-editoras {
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
