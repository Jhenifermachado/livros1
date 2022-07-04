<template>
  <header>
    <div class="menu-esquerdo">
      <span><RouterLink to="/">Home</RouterLink></span>
      <span>|</span>
      <span><RouterLink to="/livros">Livros</RouterLink></span>
      <span>|</span>
      <span><RouterLink to="/editoras">Editoras</RouterLink></span>
      <span>|</span>
      <span><RouterLink to="/categorias">Categorias</RouterLink> </span>
      <span>|</span>
      <span><RouterLink to="/autores">Autores</RouterLink> </span>
    </div>
  </header>
</template>
Template
<style>
header {
  height: 30%;
  color: rgb(255, 255, 255);
  font-size: 1.3rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-left: 200px;
}
</style>
