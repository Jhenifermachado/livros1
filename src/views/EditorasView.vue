<script>
import axios from "axios";
export default {
  data() {
    return {
      editoras: [],
      novo_editora: "",
    };
  },
  async created() {
    const editoras = await axios.get("http://localhost:4000/editoras");
    this.editoras = editoras.data;
  },
  methods: {
    async salvar() {
      const editora = {
        nome: this.novo_editora,
      };
      const editora_criado = await axios.post(
        "http://localhost:4000/editoras",
        editora
      );
      this.editoras.push(editora_criado.data);
    },
    async excluir(editora) {
      await axios.delete(`http://localhost:4000/editoras/${editora.id}`);
      const indice = this.editoras.indexOf(editora);
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
      <input
        type="text"
        placeholder="Nome"
        v-model="novo_editora"
        @keydown.enter="salvar"
      />
      <input
        type="text"
        placeholder="site"
        v-model="novo_site"
        @keydown.enter="salvar"
      />
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
              <button @click="excluir(editora)">Excluir</button>
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
  width: 200%;
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
