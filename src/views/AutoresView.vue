<script>
import { v4 as uuidv4 } from "uuid";
export default {
  data() {
    return {
      autores: [
        { id: "0888117a-25c4-40b0-b96c-0daeb8c946fb", nome: "Stephen King" },
      ],
      novo_autor: "",
    };
  },
  methods: {
    salvar() {
      if (this.novo_autor !== "") {
        const novo_id = uuidv4();
        this.autores.push({
          id: novo_id,
          nome: this.novo_autor,
        });
      }
    },
    excluir(autor) {
      const indice = this.autores.indexOf(autor);
      this.autores.splice(indice, 1);
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
  border-collapse:separate;
  margin: 0 auto;
  border: 1px solid rgb(49, 185, 8);
  font-size: 1.3rem;
  text-align: center;
}
table thead {
  background-color: rgb(21, 190, 6);
  color: rgb(38, 189, 0);
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
    background: rgb(0,22,36);
background: linear-gradient(176deg, rgba(0,22,36,1) 0%, rgba(9,121,29,1) 35%, rgba(69,255,0,1) 100%);
}
</style>

