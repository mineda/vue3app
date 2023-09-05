<template>
  <div class="about">
    <h1>{{ nome }}, hoje é Terça-Feira!</h1>
    <input type="number" v-model="contador"/>
    <button @click="incrementar">Incrementar</button>
    <input type="text" v-model="nome"/>
    <p v-if="nome.length > 5">Texto longo!</p>
    <p v-else>Texto curto!</p>
    <button @click="incluir">Incluir</button>
    <table>
      <thead>
        <td>Id</td>
        <td>Nome</td>
      </thead>
      <tbody>
        <tr v-for="usuario in usuarios" :key="usuario.id">
          <td>{{ usuario.id }}</td>
          <td>{{ usuario.nome }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup lang="ts">
  import { ref } from 'vue';
  const nome = ref("Nome");
  const usuarios = ref([{id:1, nome:"Zé"}, {id:2, nome:"Paula"}]);
  const contador = ref(1);

  function incrementar() {
    contador.value++;
  }

  function incluir() {
    usuarios.value.push({id:contador.value, nome: nome.value});
  }
</script>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
