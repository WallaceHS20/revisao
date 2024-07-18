
<template>
    <v-text-field hide-details="auto" v-model="email" label="E-mail"/>
    <v-text-field hide-details="auto" v-model="senha" label="Senha"/>
    <v-text-field hide-details="auto" v-model="cargo" label="Senha"/>
    <button @click="loginUser">Enviar</button>
    <button @click="editUser">Atualizar</button>


</template>

<script setup>

import axios from 'axios'
import { ref, onMounted } from 'vue'

const email = ref()
const senha = ref()
const cargo = ref()

async function loginUser() {
  try{
    const response = await axios.post('https://reqres.in/api/login', {
      email: email.value,
      password:senha.value
    })

    console.log(response.data);
  }
  catch(e){
    console.log(e);
  }
}

async function editUser() {
  try{
    const response = await axios.post('https://reqres.in/api/users/2', {
      email: email.value,
      job:cargo.value
    })

    console.log(response.data);
  }
  catch(e){
    console.log(e);
  }
}

</script>