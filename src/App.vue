<template>
  <h1>Sealution frontend</h1>
  <input type="text" v-model="databaseName" placeholder="create database">
  <button @click="onCreateDBClick"> Create database </button>
</template>

<script setup>
import { ref } from 'vue';
const databaseName = ref("");
async function onCreateDBClick() {
  const name = databaseName.value;
  if (name.includes(' ')) {
    console.log('name cannot contain spaces');
    return;
  }
  console.log(name);
  const result = await fetch(`${process.env.VUE_APP_BACKEND_URL}/v1/database/${name}`);
  console.log(result);
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
