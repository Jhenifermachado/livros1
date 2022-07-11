<script>
import axios from "axios";
export default {
  data() {
    return {
      autores: [],
      novo_autor: "",
    };
  },
  async created() {
    const autores = await axios.get("http://localhost:4000/autores");
    this.autores = autores.data;
  },
  methods: {
    async salvar() {
      const autor = {
        nome: this.novo_autor,
      };
      const autor_criado = await axios.post(
        "http://localhost:4000/autores",
        autor
      );
      this.autores.push(autor_criado.data);
    },
    async excluir(autor) {
      await axios.delete(`http://localhost:4000/autores/${autor.id}`);
      const indice = this.autores.indexOf(autor);
      this.categorias.splice(indice, 1);
    },
  },
};
</script>
<template>
  <div class="container">
    <div class="title">
      <h2>Autores</h2>
    </div>
    <div class="form-input">
      <input
        type="text"
        placeholder="Nome"
        v-model="novo_autor"
        @keydown.enter="salvar"
      />
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-autores">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="autor in autores" :key="autor.id">
            <td>{{ autor.id }}</td>
            <td>{{ autor.nome }}</td>
            <td>
              <button>Editar</button>
              <button @click="excluir(autor)">Excluir</button>
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
  border: 1px solid rgb(59, 190, 7);
  border-radius: 70px;
  border: 3px solid rgb(49, 185, 8);
}
.form-input {
  display: flex;
  justify-content: center;
  margin: 2rem 0;
}
.form-input input {
  width: 30%;
  padding: 0.7rem;
  border: 1px solid rgb(59, 190, 7);
  border-radius: 70px;
}
.form-input button {
  padding: 0.5rem;
  width: 10%;
  border: 1px solid rgb(84, 216, 7);
  border-radius: 70px;
  background-color: rgb(0, 0, 0);
  color: white;
  border: 1px solid rgb(59, 190, 7);
  border-radius: 700px;
  margin-left: 10px;
}
.list-autores {
  display: flex;
  justify-content: center;
}
table {
  width: 800%;
  border-collapse: separate;
  margin: 0 auto;
  border: 1px solid rgb(49, 185, 8);
  font-size: 1.3rem;
  text-align: center;
}
table thead {
  background-color: rgb(35, 239, 17);
  color: rgb(54, 255, 4);
  font-size: bold;
}
table thead th {
  background-color: rgb(48, 190, 19);
  color: whitesmoke;
}
table tbody tr:nth-child(odd) {
  background-color: rgb(125, 223, 86);
}
body {
  background: rgb(0, 22, 36);
  background: linear-gradient(
    176deg,
    rgba(0, 22, 36, 1) 0%,
    rgba(9, 121, 29, 1) 35%,
    rgba(69, 255, 0, 1) 100%
  );
}
</style>
