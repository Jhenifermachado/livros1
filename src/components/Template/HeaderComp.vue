<template>
  <header>
    <div class="menu-esquerdo">
      <span><RouterLink to="/">Home</RouterLink></span>
      <span>|</span>
      <span><RouterLink to="/livros">Livros</RouterLink></span>
      <span>|</span>
      <span><RouterLink to="/editoras">Editoras</RouterLink></span>
    </div>
  </header>
</template>
Template
<style>
header {
  height: 10%;
  background-color: #db7093;
  color: black;
  font-size: 1.3rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-left: 20px;
}
</style>
